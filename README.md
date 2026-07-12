GNSS Radio Occultation & Scatterometer Time-averaged geographical mean for Bending angles from GNSS-RO

Thanks especially to the ECMWF, ASTRAGRAPH, KeepTrack, ROM-SAF Group that allows us these analyzes with publicly available data!

https://www.ecmwf.int/ , http://astria.tacc.utexas.edu/AstriaGraph/, http://astria.tacc.utexas.edu/AstriaGraph/, https://rom-saf.eumetsat.int/

Obviously, there will be several fixes to be made, and the code isn't clean, and you will find entities that appear to be false positives but are not always false positives. I consider the exercise very interesting for various levels of understanding, knowledge and technicalities.

⚠️ Attention: there is an operator in an iFrame here that tries to open, redirect, or pop up GitHub pages that require login.

As always, you can use the plain HTML locally 👋👋👋


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/e5a57ecf-4b4e-4835-8185-a86840400d76" />


To preview GitHub HTML files, use these services by pasting the links:

https://raw.githack.com/ (Tested / working 75%)

Fast Link:

https://rawcdn.githack.com/GiamMaBasedResearchers/GNSS-RO-Multi-Portal--GNSS-Radio-Occultation-Scatterometer/f0bb2949f0cf3cb05f747712a6e8edf48566bf8e/GNSS-RO_FUll.html

Thanks to:

https://github.com/neoascetic/rawgithack

⚠️ Attention: It seems that AstriaGraph does not support some network rules, you can use the code fully locally.


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/3b1ab34b-4821-4868-bf54-c104d56f2fe2" />


GNSS-RO Multi-Portal — RFI & Anomaly Detection Dashboard


<img width="1920" height="1080" alt="image" src="https://github.com/user-attachments/assets/831e02d6-90ec-4927-a035-9b4b1bdbb0db" />


Real-time multi-source monitoring for Radio Frequency Interference (RFI), signal anomalies, and data quality degradation in GNSS Radio Occultation observations.

A unified, single-page dashboard aggregating live feeds from ECMWF, EUMETSAT ROM-SAF, space situational awareness platforms, and an interactive 3D anomaly globe — designed for researchers investigating RFI impacts on GNSS-RO bending angle and refractivity measurements.
Purpose & Scientific Context

GNSS Radio Occultation (GNSS-RO) is a critical remote sensing technique for atmospheric profiling. However, RFI (Radio Frequency Interference) — whether from ground-based transmitters, satellite uplinks, jamming devices, or space weather-induced disturbances — can systematically corrupt RO observations, introducing:

     Spurious bending angle deviations at specific altitudes
     Increased standard deviation in geographical mean statistics
     Systematic bias between constellation segments or receiving sensors
     Spatially correlated quality degradation over specific regions

This dashboard provides real-time cross-referencing between independent monitoring systems to rapidly identify, localize, and characterize such anomalies.
Portal Descriptions

1. AstriaGraph · TACC / KeepTrack / ROM-SAF (Top-Left Panel)

Space Situational Awareness + RO Monitoring Maps

Three switchable views for contextual awareness:

     

    AstriaGraph (TACC) — Live space object tracking graph. Useful for correlating RO anomalies with close approaches, conjunction events, or abnormal satellite maneuvers that could indicate onboard RFI sources or payload issues.
     

    KeepTrack — Alternative space tracker with different sensor fusion. Cross-reference with AstriaGraph to validate positional data of suspected RFI-emitting objects.
     

    ROM-SAF (EUMETSAT) — Direct access to ROM-SAF monitoring maps. These maps are a primary indicator of GNSS-RO data quality. Key anomaly markers to watch:
    ROM-SAF Indicator
    	
    RFI Relevance
    Increased bending angle variability	Suggests localized RFI corrupting phase measurements at specific ray tangent points
    Anomalous refractivity patterns	Refractivity derived from bending angles; anomalies here cascade from upstream RFI contamination
    Quality degradation flags	Broad indicator — may include RFI but also hardware/firmware issues
    Suspect data markers	Highest-priority flag — specific profiles flagged as unreliable, often RFI-related in L-band
     

     

2. ECMWF · GNSS-RO Count (Top-Right Panel)

Observation Density Monitor

Direct embed from ECMWF Charts showing the geographical distribution of GNSS-RO assimilated observations. Why it matters for RFI detection:

     Sudden drop in observation count over a specific region may indicate systematic rejection of RFI-contaminated profiles by ECMWF's quality control
     Asymmetric count patterns between ascending/descending nodes can reveal directional RFI sources (e.g., ground-based jamming affecting only westward-looking limbs)
     Temporal evolution of count anomalies helps distinguish RFI events (sharp onset/offset) from natural variability (gradual)

3. ECMWF · System Comparison (Middle-Right Panel)

Multi-Constellation Bias & Spread Analysis

This chart compares normalized departure statistics across all GNSS-RO data streams assimilated at ECMWF. Critical for RFI attribution:
ECMWF Indicator
	
RFI Interpretation
Increased standard deviation for a specific constellation	That constellation's L-band receiver may be experiencing RFI, or its transmitter signals are being jammed en route
Bias shift between GPS, Galileo, or other GNSS	Differential RFI affecting one frequency band (L1 vs L2 vs L5) causes C/A-free bending angle bias — a classic RFI signature
Outlier clusters in geographical mean	Spatially coherent outliers strongly suggest regional RFI rather than random measurement noise
Data anomaly flags	ECMWF's own QC flagging RFI-contaminated profiles before assimilation — direct evidence of RFI impact on NWP
 
 
4. GNSS-RO Satellite Catalog (Bottom-Left Panel)

Complete NORAD-ID Reference for All Active RO Satellites

A categorized catalog of every known GNSS-RO payload in orbit, with:

     NORAD IDs with one-click copy and direct N2YO tracking links
     Status indicators: ● Active · ● Degraded · ● Unconfirmed
     Constellation groupings: METOP/GRAS, COSMIC-2/TGRS, Spire/SGNSS-RO, GNOMES, FY-3/GNOS, PAZ/ROHP-PAZ, Sentinel-6, GRACE-FO, KOMPSAT-5

RFI use case: When ECMWF or ROM-SAF shows anomalies, use this catalog to immediately identify which specific satellite(s) and payload(s) are affected, then track them in real-time via N2YO to correlate with ground tracks over suspected RFI regions.
5. GNSS-RO Anomaly Globe (Bottom-Right Panel)

Interactive 3D Sphere Projection of Anomaly Layers

Upload ECMWF anomaly map PNGs (extracted via jsonlink.io from ECMWF level pages) and project them onto a rotating 3D Earth:

     Sphere projection mode — Anomaly maps wrapped on a wireframe globe with adjustable spacing, opacity, and per-layer visibility for altitude-resolved RFI visualization
     Flat heatmap mode — Composite overlay of all 29 altitude layers using additive blending for integrated anomaly intensity
     Crop controls — Remove ECMWF chart chrome (legends, colorbars) for clean projection
     Mouse coordinate readout — Hover to get exact lat/lon of anomaly features for RFI source triangulation

RFI Detection Workflow
text
 
1. SPOT  →  ECMWF System Comparison shows increased std dev for GPS stream
2. LOCATE  →  ECMWF Count map reveals observation drop over Southeast Asia
3. VERIFY  →  ROM-SAF maps confirm "suspect data" flags in same region
4. ATTRIBUTE  →  Satellite Catalog identifies affected COSMIC-2 E1-E6 payloads
5. TRACK  →  N2YO links show satellites passing over known jamming areas
6. VISUALIZE  →  Anomaly Globe projects altitude-resolved anomaly maps
7. CORRELATE  →  AstriaGraph checks for nearby RF-emitting satellite conjunctions
 
 
Technical Notes

     No backend, no API keys — All data comes from public embeddable iframes and client-side processing
     Single HTML file — Zero dependencies to install; open in any modern browser
     ECMWF charts are loaded via direct iframe embed from charts.ecmwf.int (requires internet access; some institutional networks may block)
     Three.js globe runs entirely client-side via CDN import; image URLs are loaded cross-origin from ECMWF servers
     Fullscreen mode available on every panel for detailed inspection

Constellations Monitored
Constellation
	
Payload
	
Satellites
	
Agency
METOP-SG	GRAS / GRAS-NG	METOP-B, C, D	EUMETSAT
COSMIC-2 / FORMOSAT-7	TGRS	6 satellites (E1-E6)	NSPO / NOAA
Spire Lemur-2	SGNSS-RO	100+ CubeSats	Spire Global
GNOMES	Tri-GNSS RO	GNOMES 1-5	PlanetiQ
FY-3	GNOS-1/2	FY-3D, FY-3E	CMA
PAZ	ROHP-PAZ	PAZ	INTA / Hisdesat
Sentinel-6	POSEIDON-4/RO	Sentinel-6A	ESA / NASA / NOAA
TerraSAR-X / TanDEM-X	IGOR	2 satellites	DLR
GRACE-FO	GNSS-POD/RO	GRACE-C, GRACE-D	NASA / DLR
KOMPSAT-5	AOPOD-RO	1 satellite	KARI
 
 
Links

     ECMWF Observation Statistics: charts.ecmwf.int
     ROM-SAF Monitoring: rom-saf.eumetsat.int
     AstriaGraph: astria.tacc.utexas.edu
     KeepTrack: app.keeptrack.space
     Image URL Extractor: jsonlink.io
     Satellite Tracking: n2yo.com

Author

GiamMa SDR R&D IoT — @GiammaIoT2 - https://x.com/giammaiot2/

GNSS-RO based research · Software Defined Radio · Radio Frequency Interference monitoring · IoT

⚠️ Disclaimer

Disclaimer: The code is for educational, training, analysis, & security purposes, & is intended for understanding & knowledge. The authors assume no liability for the misuse of this tool or the data it visualizes. Always ensure you have permission to access and visualize telemetry data.

Credits

This code provide from: "GiamMa-based researchers SDR R&D IoT" | @GiammaIoT2 License

This project is provided for research and educational purposes.
