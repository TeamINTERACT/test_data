# Test data description for INTERACT data pipeline

Test data will be used to develop code base and trouble shoot code on full deployment of the data. These data are not full data but represent data from 6 participants from Saskatoon and Montreal in Wave 1 and Wave 2. Some participants have data some data, some do not. I tried to create as many cases as possible with some participants having data in W1 and not W2 and vice versa. Some have 2 .sdb files, etc.

The goal of the test_data is to run the full data pipeline. The full data pipeline description and documentation is available here [https://github.com/TeamINTERACT/data_pipeline](https://github.com/TeamINTERACT/data_pipeline).

# Data Pipeline 

These data relate to sensor data files from data pipeline. Descriptions of these files are below.

* Linkage
    * Participation meta-data for each data source, participants are assigned an ID. These are tracked through the city's linkage file (one linkage file per city, per wave)
* SenseDoc
    * The SenseDoc is a research grade multisensor device used for mobility (GPS) and physical activity (accelerometer) tracking. These data are collected continuously and allow us to measure location-based physical activity and infer transportation mode.
* Ethica
    * Ethica is a research-grade smartphone app used for mobility and physical activity tracking. These data are collected in a 1-in-5 duty cycle (1 minute active, 4 minutes idle). It collects
        * GPS
        * WiFi signals
        * Activity recognition
        * Pedometer
        * Battery
        * Accelerometer data

# Folder structure

* City
    * Wave
        * File - `linkage_wave_01_saskatoon.csv`. Test linkage file (6 participants) for each wave.
        * File - `saskatoon_w1_test_data_code.Rmd`. R Markdown file with the code I used to create the data. Only useful if I made a mistake and we need to go back and check something.
      * Folder - `Ethica`
        * Folder - `interact_id` Participant unique interact_id
            * Files - One file for each sensor formatted as `datatype_wave_datasource.csv` 
              * Example files names
                * `accel_wave_01_ethica.csv`
                * `battery_wave_01_ethica.csv`
                * `gps_wave_01_ethica.csv`
                * `mbar_wave_01_ethica.csv`
                * `pedemeter_wave_01_ethica.csv`
      * Folder - `sensedoc.zip`
        * `interact_id` Participant unique interact_id
            * Example files names  
              * `SD324fw2099_20210415_105014.sdb`

# Test data code

## Saskatoon

* Wave 1 Saskatoon data creation code is available here [https://github.com/TeamINTERACT/test_data/blob/main/saskatoon_w1_test_data_code.Rmd](https://github.com/TeamINTERACT/test_data/blob/main/saskatoon_w1_test_data_code.Rmd)
* Wave 2 Saskatoon data creation code is available here [https://github.com/TeamINTERACT/test_data/blob/main/saskatoon_w2_test_data_code.Rmd](https://github.com/TeamINTERACT/test_data/blob/main/saskatoon_w2_test_data_code.Rmd)

## Montreal

* Wave 1 Montreal data creation code is available here [https://github.com/TeamINTERACT/test_data/blob/main/montreal_w1_test_data_code.Rmd](https://github.com/TeamINTERACT/test_data/blob/main/montreal_w1_test_data_code.Rmd)
* Wave 2 Montreal data creation code is available here [https://github.com/TeamINTERACT/test_data/blob/main/montreal_w2_test_data_code.Rmd](https://github.com/TeamINTERACT/test_data/blob/main/montreal_w2_test_data_code.Rmd)

# Pipeline Steps

  * Collect: Data is collected from participants
  * Extract: Data is imported from original data source and moved to Compute Canada
    * BACKUP
  * Validate: Data is verified to ensure correct format and meta data. Any data issue is flagged to the research team and fixed at this step before continuing through the pipeline. If corrections occur, data is backed up to nearline, replacing the previous back-up.
  * Load: Data is loaded by developer.
  * Transform: Data is cleaned or transformed as needed.
    * OUTPUT: Elite files (flat tables of intermediary files for expert members of team)
  * Produce: Data is outputed as flat tables used by larger research team. For SD and Ethica, these are the Tables of Power.
    * OUTPUT: Create csvs of Polygon surveys or ToP, for SenseDoc or Ethica
  * Describe: Data is described with summary statitsics to help check data is as expected.
  
![](https://user-images.githubusercontent.com/48290593/252497954-1e459533-74ee-4e2c-942d-29013f293dcd.png)



