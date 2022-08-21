# Categorise_CME
2022 Aberystwyth university AI summer school. My code to categorise CMEs into geoeffective or not


## The Data
The data has been collected from [OMNIWeb](https://omniweb.gsfc.nasa.gov/form/dx1.html) 

- Date: The UTC date for when the CME was detected in Space
- Time: UTC time of detection 
- DST: Disturbance Storm Time measured in nT 
- Disturbance_date: The date when detected on earth
    - This gets encoded into 1 (>100nT) and 0 (<100nT) into the Dst_label column
    - This is the 'Label', 1 or 0
- Disturbance_time: The time when detected on earth

There are then 23 measured parameters for the:
- Magnetic field
    - B(IMF): IMF magnitude average , nT
    - Vector_B: Magnitude, Avg IMF, nT
    - Lat_angle_B: Latitude of average IMF, degrees
    - Long_angle_B: Longitude of average IMF, degrees
    - Bz(GCE): 
    - Bz(GSM): z component of Geocentric Solar Magnetospheric
    - RMS_magnitude: error of magnetic field
    - RMS_field_vector: error of field vector
    - RMS_BZ_GSE: error of z component of GSE field
- Plasma
    - Plasma_Temp: temperature of plasma
    - Proton_Density: the density of protons in the cme
    - Plasma_speed: speed of plasma
    - Alpha/proton: ratio of alpha particles to protons
    - sigma-T 
    - sigma-n
    - sigma-V
    - sigma-ratio
    - flow_pressure: The pressure
    - E_field: electric field
    - Plasma_beta
- Indices
    - Kp_index
    - Ap_index 

## The labels
The labels are based off the DST value of the event. A different DST value will cause different types of geomagnetic storms when the event reaches earth.
- 50 -100 is moderate -> label is 0 (not geoeffective)
- 100- 250 is storm -> label is 1 (geoeffective)
- 250+ is extreme -> for logistic regression the label is 1 aswell, if a mlp is used then it can be labelled 2
