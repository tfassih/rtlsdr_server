# rtlsdr_server

# Data Structure of ADS-B messages as per the ICAO standard
+----------+----------+-------------+------------------------+-----------+
|  DF (5)  |  CA (3)  |  ICAO (24)  |         ME (56)        |  PI (24)  |
+----------+----------+-------------+------------------------+-----------+

# Bit		No. bits	Abbreviation	Information
--------------------------------------------------------------------------
1–5		    5			      DF				Downlink Format
6–8		    3			      CA				Transponder capability
9–32	    24			    ICAO			ICAO aircraft address
33–88	    56			    ME				Message, extended squitter
(33–37)	  (5)			    (TC)			(Type code)
89–112	  24			    PI				Parity/Interrogator ID

# CA		Definition
--------------------------
0		  Level 1 transponder
1–3		Reserved
4		  Level 2+ transponder, with ability to set CA to 7, on-ground
5		  Level 2+ transponder, with ability to set CA to 7, airborne
6		  Level 2+ transponder, with ability to set CA to 7, either on-ground or airborne
7		  Signifies the Downlink Request value is 0, or the Flight Status is 2, 3, 4, or 5, either airborne or on the ground

# Type Code	  Dataframe content
---------------------------------------
1–4			    Aircraft identification
5–8			    Surface position
9–18		    Airborne position (w/Baro Altitude)
19			    Airborne velocities
20–22		    Airborne position (w/GNSS Height)
23–27		    Reserved
28			    Aircraft status
29			    Target state and status information
31			    Aircraft operation status

Messages					        TC			    Ground (still)		Ground (moving)		Airborne
------------------------------------------------------------------------------------------
Aircraft identification		1–4			      0.1 Hz				      0.2 Hz				 0.2 Hz
Surface position			    5–8			      0.2 Hz				      2 Hz					    -
Airborne position			    9–18, 20–22		  -				            -					   2 Hz
Airborne velocity			    19				      -				            -					   2 Hz
Aircraft status				    28			      0.2 Hz (no TCAS RA and Squawk Code change) / 1.25 Hz (change in TCAS RA or Squawk Code)
Target states and status	29				      -			            	-					    0.8 Hz
Operational status			  31			      0.2 Hz				0.4 Hz (no NIC/NAC/SIL change) / 1.25 Hz (change in NIC/NAC/SIL)

