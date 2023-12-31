# AI Based Industrial Device Condition Monitoring

## Summary
| Company Name | [Osaühing Pentamet](https://www.pentamet.ee) |
| :--- | :--- |
| Development Team Lead Name | [Dr. Argo Rosin](https://www.etis.ee/CV/Argo_Rosin/eng/) |
| Development Team Lead E-mail | [argo.rosin@taltech.ee](mailto:argo.rosin@taltech.ee) |
| Objectives of the Demonstration Project | Develop a solution for production equipment failure prediction. |
| Final Report | [Tehnoloogiline_Aruanne_Final.pdf](https://github.com/ai-robotics-estonia/ai-based_industrial_device_condition_monitoring/files/13800696/Tehnoloogiline_Aruanne_Final.pdf); [Tagasiside_TehnoloogiliseleAruandele_final.pdf](https://github.com/ai-robotics-estonia/ai-based_industrial_device_condition_monitoring/files/13800695/Tagasiside_TehnoloogiliseleAruandele_final.pdf); [Demoproject_report_#1.pdf](https://github.com/ai-robotics-estonia/ai-based_industrial_device_condition_monitoring/files/13800694/Demoproject_report_.1.pdf); [Demonstration-Project_Report_#2_updated_final.docx.pdf](https://github.com/ai-robotics-estonia/ai-based_industrial_device_condition_monitoring/files/13800693/Demonstration-Project_Report_.2_updated_final.docx.pdf) |

# Description
## Objectives of the Demonstration Project
*Please describe your project objectives in detail.*

The aim of the demoproject is to develop a solution based on artificial intelligence that can predict the failure of production equipment and reduce the need for unscheduled maintenance. Currently, development work is underway at the plant of Pentamet OÜ, where process control and electrical monitoring systems have been implemented. The intelligent monitoring solution uses artificial intelligence to predict and show potentially problematic machines that need preventive maintenance. The developed solution can be easily further developed for application in similar industries.

For details, check the [final report](#summary).

## Activities and Results of the Demonstration Project
### Challenge
*Please describe challenge addressed (i.e, whether and how the initial challenge was changed during the project, for which investment the demonstration project was provided).*

Many industrial sectors are moving toward Industry Revo- lution (IR) 4.0. In this respect, the Internet of Things and predictive maintenance are considered the key pillars of IR 4.0. Predictive mainte- nance is one of the hottest trends in manufacturing where maintenance work occurs according to continuous monitoring using a healthiness check for processing equipment or instrumentation. It enables the maintenance team to have an advanced prediction of failures and allows the team to undertake timely corrective actions and decisions ahead of time. The aim of this report is to present a smart monitoring and diagnostics system as an expert system that can alert an operator before equipment fail- ures to prevent material and environmental damages. The main novelty and contribution of this report is a flexible architecture of the predictive maintenance system, based on software patterns - flexible solutions to general problems. The presented conceptual model enables the integra- tion of an expert knowledge of anticipated failures and the matrix-profile technique based anomaly detection. The results so far are encouraging.

Keywords: predictive maintenance · conceptual architecture · analysis patterns · machine learning · time series analysis · matrix profile.

For details, check the [final report](#summary).

### Data Sources
*Please describe which data was used for the technological solution.*  
- Temperature sensors data, 12 measurement points, -50 ... 500 °C;
- 3 axis vibration sensors data, 2 measurement points, 0,7 Hz ... 4 kHz, ±10 g.

For details, check the [final report](#summary).

### AI Technologies
*Please describe and justify the use of selected AI technologies.*
- Anomaly detection is based on the Matrix Profile method by searching for motifs (i.e. recurring patterns) from time-series data and finding minimal Euclidean distance between any sub-sequence. To detect anomalies thresholds are calculated by using matrix profile data of a healthy expansion joint;
- Evaluation and validation of the developed solution were done by running an experiment on a test bench where an expansion joint was cyclically aged until it ruptured. The experiment lasted for 3 days during which all the data was recorded and camera recordings were used for visual inspection of the expansion joint condition. By comparing the diagnostic solution output with recordings it was found that the developed solution can detect rupture when it appears.

We make heavy use of a Matrix Profile (MP) method in our predictive main- tenance system. While our architecture is general and can work with different methods, it is an effective method and an excellent example to explore the issues of time series analysis.
Time series analysis typically looks at anomalies and motifs/ patterns. The basic idea of MP is to calculate the distance between pairs of sub-sequences in the time series by computing the distance between each pair. An important parameter for MP is the window size: length of sub-sequences. Despite the sim- plicity of a naive algorithm based on nested loops, it can take years or months to get an answer for a moderately sized time series using this method. However, using the Matrix Profile algorithms, computation time is significantly reduced. It is a relatively new time series analysis data structure invented by Eamonn Keogh [10] at the University of California Riverside, and Abdullah Mueen at the University of New Mexico [16]. A matrix profile is a vector that stores the z-normalized Euclidean distance between any sub-sequence within a time series and its nearest neighbor. This algorithm is agnostic to domains, fast, supplies an exact solution, and only requires one parameter (window size).
Below we show at the top a synthetic time series from a temperature sensor, which contains two sawtooth patterns and added noise. Temperature is standardized to the mean of zero and standard deviation of one. At the bottom we show the corresponding Matrix Profile values for sub-sequences of the length 640. MP values correspond to distance to nearest (most similar) sub-sequence and therefore low MP values show repeating motifs. As we can see, these identify our two sawtooth patterns. Anomalies can correspondingly be identified by large MP values as shown below.

<img width="467" alt="Screenshot 2023-12-31 at 11 29 59" src="https://github.com/ai-robotics-estonia/ai-based_industrial_device_condition_monitoring/assets/15941300/79bd92bd-c340-478d-8bc8-f1e32e8daa0e">
<img width="460" alt="Screenshot 2023-12-31 at 11 26 16" src="https://github.com/ai-robotics-estonia/ai-based_industrial_device_condition_monitoring/assets/15941300/21c25fb4-0d77-4996-9fb1-fc98a44eaa74">


For details, check the [final report](#summary).

### Technological Results
*Please describe the results of testing and validating the technological solution.*

- Diagnostic system architecture. The developed solution and conducted analysis give guidelines for sensors selection, location, installation, and how to acquire and preprocess the data. All the data was visualized and management of alerts was done by using the Grafana observability platform;
- Sensor network self-diagnostics. The solution detects each sensor condition that is not normal, alerts the system operator, and proposes actions to take;
- The component of interest (e.g. expansion joint) condition monitoring. The solution detects anomalies in time series data and alerts the system operator which initiates the inspection of the component.

For details, check the [final report](#summary).

### Technical Architecture
*Please describe the technical architecture (e.g, presented graphically, where the technical solution integration with the existing system can also be seen).*

We describe the conceptual pattern-based architecture for predictive mainte- nance using UML class diagrams. We base this on known analysis patterns [4] and architectural patterns [2].

#### Domain Modeling, UML Class diagrams and Patterns
First, we introduce the main ideas of domain modeling. The domain is any field that computation can be applied to [11]. Domain (Conceptual) modeling aims to identify, detect and define the concepts from the domain. The latter are usu- ally but not always, mirrored within the computational system. For example, in a healthcare system, we may identify concepts like Patient, Observation, Pro- tocol, etc. [4]. In the field of trading, we can identify concepts like Derivative Contract, Contract, Portfolio, Trading Package, etc. [4]. Potential concepts can be at a higher or lower level of abstraction (Measurement vs. Blood Pressure Measurement) and be more or less relevant for certain goals (Blood Pressure Measurement is not relevant for the goals of Trading but relevant for Health- care). Models are not right or wrong, but more or less valuable [4]. However, models that describe confusing concepts or are not general enough can make extending, scaling, and changing a system a nightmare. General models used in many different domains and named and described in the literature are called patterns. Patterns are meant to help with describing and proliferating good de- sign practices [4]. They are widely used in software engineering, but with the rapidly increasing complexity of AI systems like predictive maintenance, they should become more relevant.
A visual way to describe domain concepts is through class diagrams of Uni- fied Modeling Language (UML) [1]. Class diagrams can describe either domain concepts or software classes. We provide a short explanation of this notation below.

<img width="784" alt="Screenshot 2023-12-31 at 11 32 04" src="https://github.com/ai-robotics-estonia/ai-based_industrial_device_condition_monitoring/assets/15941300/c85c2b07-9d51-418a-aa6f-81463999e952">

#### Patterns for Predictive Maintenance
A system of predictive maintenance should ideally combine the expert knowl- edge with the power of AI systems like MP to detect outliers and anomalies. Our aim is common with the field of software engineering: to protect the system from variations arising from changing user requirements.We do not want to change, reprogram and redeploy our system when user tolerance for false positives and false negatives changes, when user decides that certain indicator is not useful anymore etc. Therefore we introduce a rule interpreter that allows user/expert to add, change and delete various alert rules, controlling the behaviour of our system. We also note that these rules could apply to both actual sensor ob- servations and machine learning anomaly/motif estimates derived from those observations. Therefore we generalize both of those into Indicators. Our general split between expert defined rules and various indicators that these rules apply to was present before we made the connection to the patterns from the field of software engineering but this connection has enabled us to clarify and generalize our approach. As it is common with patterns we have modified them to suit the needs of our specific field of predictive maintenance.

For details, check the [final report](#summary).

### User Interface 
*Please describe the details about the user interface(i.e, how does the client 'see' the technical result, whether a separate user interface was developed, command line script was developed, was it validated as an experiment, can the results be seen in ERP or are they integrated into work process)*

Grafana.

For details, check the [final report](#summary).

### Future Potential of the Technical Solution
*Please describe the potential areas for future use of the technical solution.*

Key assumptions for potential implementation(s):
- Condition monitoring – the solution gives the ability to observe each component and related process condition where the diagnostic system is installed. Furthermore, the solution user can add his/her own rules to the already existing ones and design a dashboard according to his/her needs;
- Predictive maintenance – the solution gives more confidence to the system operator that the process and its critical components are healthy. Decreasing the need for preventive maintenance and thus reducing operational costs;
- Anomaly detection – the solution can detect any anomalies in the time-series data regardless of the source of the data. These anomalies can be directly connected to failed or fatigued components which must be repaired or replaced. Through on-time alerts, the solution prevents further damage to the process or its surroundings and thus reducing the cost of failure.

Prerequisites for potential future implementation(s):
- condition monitoring solution, e.g. SCADA system or measurement system for data collection;
- standardized interfaces for data communication.
  
Potential Sector(s):
- mechanical engineering companies;
- electrical industry companies;
- forest/Wood industry companies.

Potential Client(s):
- Tarmeko;
- Fusebox;
- Graanul Invest.

For details, check the [final report](#summary).

### Lessons Learned
*Please describe the lessons learned (i.e. assessment whether the technological solution actually solved the initial challenge).*

The report proposes a conceptual architecture that splits the system into a rule/expert system layer and an indicator/machine learning layer. This architecture is based on known patterns from the field of software engineering. It establishes expert rules on indicators from sensors and machine learning meth- ods like Matrix Profile and allows for independent, flexible evolution of rule management and machine learning subsystems. This report also presented one potential set of technologies to implement such conceptual architecture, using Grafana open observability platform, Python’s stumpy framework [8] for Matrix Profile. To the best of our knowledge the application of Rule and Observation patterns in our predictive maintenance architecture is a novel contribution.
We have already started building a scalable near-real-time platform to detect underperformance and uptake the proactive maintenance activities. We use the most cutting-edge techniques from machine/Deep learning and big data fields for that purpose.
The technical impact will be manifested through increased innovation facili- tated by new AI solutions. The architecture of near-real-time management tool offers some distinctive features :
- Velocity challenge: Provides a near real-time accurate classification of data collected (and aggregated) from multiple sources (sensors, images, videos).
- Zero-delay challenge: The early detection of underperformance is pivotal as it may have dramatic consequences.
- Scalability: Built using the open-source big data platform APACHE-SPARK; on top of it stands the most scalable event streaming platform APACHE-KAFKA (High throughput and availability).

For details, check the [final report](#summary).
