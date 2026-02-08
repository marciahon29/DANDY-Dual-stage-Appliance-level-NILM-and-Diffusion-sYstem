ABSTRACT

Traditionally, NILM (Non-Intrusive Load Monitoring) has been proposed to help save around 12% of annual electricity consumption by highlighting which appliance is active. In this paper, we seek to extend and refine this methodology by incorporating Appliance Anomaly Detection. We created DANDY (Dual-stage Appliance-level NILM and Diffusion sYstem) to identify a single anomalous appliance out of the aggregate electricity consumption of three appliances (Fridge, Dishwasher, WashingMachine). In contrast, traditional methods are restricted to an aggregate or an appliance-by-appliance approach. Our first component is a NILM model that combines Autoencoder, Cosine Similarity, and Decision Tree to perform a time series classification of “ON” / “OFF” based on a month of Smart Plug usage. Following this is the Diffusion Anomaly Detection model that identifies if a pattern is “Normal” or “Anomaly”. This framework can identify contextual anomalies and bypass the traditional and trivial 3-sigma threshold anomaly detection. Our analysis consists of fourteen datasets (7xREFIT, 3xUKDALE, 3xGREEND, 1xAMPds2), seven anomalous days (Monday, Tuesday, Wednesday, Thursday, Friday, Saturday, and Sunday), and seven synthetic anomalies (StepChange, MultiStepChange, Mirror, Repeating, StuckMAX, StuckMIN, and PowerCycling). We compare across six algorithms: 3-Sigma, Isolation Forest, DBSCAN, Autoencoder, COCA, and Diffusion. We achieved promising values for Appliance Accuracy and Anomaly Accuracy. Our project is not limited to success only in the residential sector. It may also find direct application in the commercial, manufacturing, and industrial sectors, as well as in IoT (Internet of Things), whereby the objective is proactive monitoring and identification of anomalous equipment out of a time series composite set.

EXPLANATION OF FILES (The order is the order of usage)

1. DANDY_DatasetCreation.ipynb: <br>
  a. From datasets (7xREFIT/3xUKDALE/3xGREEND/1xAMPds2) and appliances (Fridge/Dishwasher/WashingMachine), creates files with 15-minute frequency. <br>
  b. Creates the Centroids file (average active_power for Fridge/Dishwasher/WashingMachine/Nothing). <br>
  c. Creates the 7 anomalies (StepChange, MultiStepChange, Mirror, Repeating, StuckMAX, StuckMIN, and PowerCycling) for 7 days. <br>
  d. Merges normal and anomalies together while specifying ground_truth_anomaly and ground_truth_appliance. <br>

2. DANDY_AnomalyDetection_3SIGMA.ipynb

3. DANDY_AnomalyDetection_ISOLATIONFOREST.ipynb

4. DANDY_AnomalyDetection_DBSCAN.ipynb

5. DANDY_AnomalyDetection_AE.ipynb

6. DANDY_AnomalyDetection_COCA.ipynb

7. DANDY_AnomalyDetection_DIFFUSION.ipynb

8. DANDY_NILM.ipynb - perform NILM Classification

9. DANDY_Statistics.ipynb - combining Anomaly Detection with NILM and statistics.


THE HIERARCHY OF THE FOLDERS

AnomalyType is: {3SIGMA, ISOLATIONFOREST, DBSCAN, AE, COCA, DIFFUSION_RESIDUALSPECTRAL}

Paper02_14Datasets
      |
      --- REFIT_ORIGINALS
      --- UKDALE_ORIGINALS
      --- GREEND_ORIGINALS
      --- AMPds2_ORIGINALS
      |
      --- MERGED
      --- CENTROIDS
      |
      --- ANOMALY_{AnomalyType}
             |
             --- Percentiles_Summary
      --- NILM
      --- COMBINED_{AnomalyType}
      |
      --- STATISTICS
