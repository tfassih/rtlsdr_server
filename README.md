# ATAC Primary Reference Document
<h1 align="center">SUMMARY<br><h1>
<h1 align="center">ARCHITECTURE<br><h1>
<h1 align="center">ADS-B STANDARD<br><h1>
<h2 align="left">Data Structure of ADS-B messages as per the ICAO standard<br></h2>
<p align="left">
<b>+----------+----------+-------------+------------------------+-----------+ <br>
| &ensp; DF (5) &nbsp;  | &nbsp; CA (3) &ensp; | &ensp; ICAO (24) | &ensp; &emsp; &emsp; ME (56) &emsp; &emsp; | &emsp; PI (24) &nbsp; | <br>
+----------+----------+-------------+------------------------+-----------+ </b><br>
</p>

<p align="left">
<b>Bit	No. &emsp; Bits &emsp; Abbreviation	&emsp; Information</b><br>
1–5		&emsp;&emsp;&emsp;    5			&emsp;&emsp;&emsp;      DF		&emsp;&emsp;&emsp;		Downlink Format<br>
6–8		&emsp;&emsp;&emsp;     3			&emsp;&emsp;&emsp;       CA		&emsp;&emsp;&emsp; 		Transponder capability<br>
9–32	&emsp;&emsp;&ensp;     24		&emsp;&emsp; 	    ICAO	&emsp;&emsp;&ensp; 		ICAO aircraft address<br>
33–88	&emsp;&emsp;     56		&emsp;&emsp;&ensp; 	    ME		&emsp;&emsp;&emsp; 		Message, extended squitter<br>
(33–37)	&emsp;&ensp;   (5)		&emsp;&emsp;&ensp; 	    (TC)	&emsp;&emsp;&ensp; 		(Type code)<br>
89–112	&emsp;&ensp;  24		&emsp;&emsp;&ensp; 	    PI		&emsp;&emsp;&emsp;&ensp; 		Parity/Interrogator ID<br>
</p>
<p align="left">
<b>CA	&emsp;&emsp;	Definition</b><br>
0		&emsp;&emsp;  Level 1 transponder<br>
1–3	&emsp;      	Reserved<br>
4		&emsp;&emsp;  Level 2+ transponder, with ability to set CA to 7, on-ground<br>
5		&emsp;&emsp;  Level 2+ transponder, with ability to set CA to 7, airborne<br>
6		&emsp;&emsp;  Level 2+ transponder, with ability to set CA to 7, either on-ground or airborne<br>
7		&emsp;&emsp;  Signifies the Downlink Request value is 0, or the Flight Status is 2, 3, 4, or 5, either airborne or on the ground<br>
</p>
<p align="left">
<b>Type Code	&emsp;&emsp;&emsp;&emsp;  Dataframe content</b><br>
&emsp;1–4		&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;	    Aircraft identification<br>
&emsp;5–8		&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;	    Surface position<br>
&emsp;9–18	&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;	    Airborne position (w/Baro Altitude)<br>
&emsp;19		&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;	    Airborne velocities<br>
&emsp;20–22		&emsp;&emsp;&emsp;&emsp;&emsp;    Airborne position (w/GNSS Height)<br>
&emsp;23–27		&emsp;&emsp;&emsp;&emsp;&emsp;    Reserved<br>
&emsp;28			&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;    Aircraft status<br>
&emsp;29			&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;    Target state and status information<br>
&emsp;31			&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;    Aircraft operation status<br>
</p>
<p align="left">
<b>&emsp; Messages			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;     TC			&emsp;&emsp;&emsp;&emsp;    Ground (still)	&emsp;&emsp;&emsp;&emsp;	Ground (moving)	&emsp;&emsp;&emsp;&emsp;	Airborne</b><br>
Aircraft identification	&ensp;&emsp;&emsp;&emsp;&emsp;	1–4			&ensp;&emsp;&emsp;&emsp;&emsp;      0.1 Hz			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;	      0.2 Hz		&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;		 0.2 Hz<br>
Surface position			&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;    5–8			&ensp;&emsp;&emsp;&emsp;&emsp;      0.2 Hz			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;	      2 Hz		&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;		    -<br>
Airborne position				&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;    9–18, 20–22		&ensp;&emsp;&emsp;  -				   &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;        -			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;		   2 Hz<br>
Airborne velocity			&nbsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;	    19			&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;	      -				  &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;         -			&emsp;&emsp;&emsp;&emsp;	&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;	   2 Hz<br>
Aircraft status					&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;    28			&emsp;&emsp;&emsp;&emsp;&emsp;&ensp;   0.2 Hz (no TCAS RA and Squawk Code change) / 1.25 Hz (change in TCAS RA or Squawk Code)<br>
Target states and status	&nbsp;&emsp;&emsp;&emsp;	29				&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;      -			 &emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;           	-				&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; &emsp;	    0.8 Hz<br>
Operational status			&ensp;&emsp;&emsp;&emsp;&emsp;&emsp;	  31		&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;     0.2 Hz		&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp;&emsp; 		0.4 Hz (no NIC/NAC/SIL change) / 1.25 Hz (change in NIC/NAC/SIL)<br>
</p>
