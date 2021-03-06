ALL RIGHT RESERVED © 2020 Amey Desai

# CoCo
## Corona Control
A tool to help estimate hotspots of COVID-19 infection

Please contact amey@lifesparktech.com for non-commercial uses. This is intended to prevent misuse.

## GOALS:
1) Proactive identification of critical transmission zones.
2) Identification of human-human transmission(including asymptomatic carriers) and transmission through contaminated surfaces.
2) Enable seamless communication between 3 major stakeholders (Government, Healthcare Facilities and individuals.
3) Include a 2-stage verification process for self-reporting patients to prevent false positives.
4) Enable live tracking of inventory and occupancy data for hospitals to allow bidirectional communication with the Government authorities and MoH.


## CONCEPT

The coronavirus infection has two important properties that have led to the current pandemic: exponential spread and symptoms that are similar to existing ailments{[1][2]}. It’s high infectivity is especially a cause for concern. 

Measures for reducing the impact of infection broadly hinge on one aspect: Reducing the exponent. This can be achieved through aggressive contact tracing and isolation of positive cases{[4][5]}. While testing every person is impractical, informed decisions regarding the deployment of testing and quarantine resources can substantially reduce spread and improve outcomes{[3]}.

To this end, we propose a digital platform to facilitate mass movement modelling and contact tracing aimed at providing accurate insight into resource deployment. The platform consists a web portal and a mobile app. The idea is based on a few key characteristics.

**1. Crowd-sourced data**
The scale of the problem is beyond the ability of any single agency. Data collection requires that individuals opt-in to voluntarily share their data.

**2. Privacy-first approach**
One of the most important factors affecting voluntary sign-up is privacy. Safety and privacy of the individual with respect to each stakeholder (other individuals, health authorities), is a basic requirement.

**3. Proactive deployment of resources**
The general approach to contact tracing is retrospective. When implemented digitally through approaches such as Singapore’s TraceTogether, this effectively helps find and isolate potential cases. However, this approach only tackles direct human-to-human proximity based spread. Other means of spread, such as through contaminated surfaces in public places, or through food, etc are not
tracked by this method. Our platform also prioritizes GPS-based movement data to spot points of convergence in location trails of individuals, helping unearth such hard-to-find sources.

**4. Closed Loop System**
Government officials need a sense of the situation on the ground to operate effectively. In particular, they need to be made aware of the inventory and patient load at hospitals. 

The prevalence of smartphones and the internet makes mobile applications ideal candidates for this method of data collection. Our data-driven platform uses crowdsourced anonymized location data and Bluetooth proximity data from a user’s cellphone, along with demographic data and lifestyle data entered by the user. This helps us in determining other people that have come in close proximity in the past 2-3 weeks (through the proximity of their cellphones) as well as places in the neighbourhood where people generally tend to visit in large numbers (supermarkets, etc). In the event that a person tests positive, resources for testing, fumigation etc. can be directed towards these local hotspots of convergence in addition to notifying those
who have come in close contact.

The demographic and lifestyle/health data collected will include prescribed drugs, preexisting conditions, other factors that can help medical professionals and epidemiologists gain more insight into clinical management and potentially aid development of vaccines.

Government officials require information about the situation on the ground at hospitals to effectively deploy resources as and when required. The web portal **Infomed.live** facilitates this need. Hospitals can update their inventory, their patient load and capacity, personnel availability, etc. regularly so that health officials can keepin touch with the situation on the ground.

![CoCo Feature Description and Flow](https://github.com/Lifespark-Technologies/CoCo/blob/master/docs/CoCo_onepage_flow_descript.png)

## PRIVACY

Most countries that have made significant headway against the epidemic have temporarily suspended privacy concerns. Singapore’s TraceTogether app traces contact between people through the proximity of their phones. The app generates random ‘Contact Event Numbers (CEN)’ which are exchanged when two devices come in close proximity with each other. These CENs are linked to user entries in a central database that are accessible to the authorities{[8]}. While this grants anonymity to individuals from each other, it does not grant them anonymity from the authorities. The system also relies on the honesty of users{[8]}. 

South Korean authorities have implemented one of the most successful screening systems in the form of drive-thru testing. While successful, it completely does away with privacy by using phone numbers to report results{[6]}. There have been cases of community ostracization and witch-hunts, which highlight the need for privacy in this matter{[6][7]}. 

Our system largely relies on self-reporting to prevent privacy intrusions. We believe that making individuals aware of the impact that the epidemic can have on not just themselves, but their families and loved ones, sufficiently incentivizes voluntary participation. Comparing various methods of collecting data, and their levels of privacy (Table 1{[8]}), we have come to the conclusion that using an encrypted, multi proxy-server based approach works best to satisfy privacy requirements and constraints for scalability.

To make the system more resilient to spam, we implement a verification system that can be completely managed through either the mobile app or through the web portal. On self-reporting (after going through the symptom tracker), the user receives a ‘Patient number’ generated by the app. This number is used to schedule an appointment through the app. This ensures there isn’t overcrowding at hospitals/test centers. The results of the test can be securely notified to the user by hospitals through the app or the web portal. This system prevents false positives.

Preventing overcrowding at hospitals is quite important. As learnt from New York, hospitals themselves can become hotspots of infection. Given the resource constrained nature of the healtchcare system in times of a pandemic, we need to ensure only as many patients visit as it is possible to manage.

## IMPLEMENTATION
### ORACLE
### Optimized Resource Allocation & Cluster Localization Estimation
### CONTACT TRACING 

Bluetooth based Proximity Detection
Bluetooth based contact-tracing works by detecting proximity between cellphones through data broadcast using the Bluetooth communication protocol. Since the Bluetooth radio protocol is meant for short-range data transfer, it aligns perfectly with such usage. 

When two phones are in close proximity, they exchange “Contact Event Numbers”, which are randomly generated numbers (tokens) unique to every such occurrence. Every phone stores all such tokens. In the event that a user reports positive, their tokens are uploaded to a public database. Every user’s phone periodically checks against these public tokens and notifies the user if any token in their list matches those of positive cases. In this case, the user is advised to test themselves. None of these tokens have any personally identifiable information. Nor are the health authorities aware of the owners of these tokens, hence testing and self-reporting are the responsibility of  the user. This method is very accurate and scalable for person-to-person transmission detection{[8]}.

### GPS 
For methods of transmission besides direct person-to-person infection, we collect GPS location data. GPS location has an accuracy of upto 2 meters. Anonymized location data from individuals is used to create a map of population movement density. This allows for detection of non-human transmission by potentially linking positive cases without contact but with common points on the location trail. With such a technique  it is possible to approximately calculate where the fomite-based risk of infection is the highest; i.e, where there may be inanimate objects capable of transmitting infection. Based on this data, a risk map of such locations can be traced to show comparative risks of different geographical areas. 

GPS data also enables determination of hyperlocal points of convergence where resources can be directed for testing and containment efforts in case an infection is detected in the neighbourhood. A proximity alert is sent to users to avoid travelling to areas where the risk of infection is high.

All GPS data is anonymized and securely sent to the main server through proxy servers. Individual trails will not be public, just their intersections and local hotspots. <ORACLE Protocol>

### HEALTH DATA
In addition to location and proximity data, we aim to include a short questionnaire in the process of building the user profile. This will comprise demographic{[9]} and health data (Age group, Gender, Pre-existing health conditions etc.) and lifestyle data (Shopping habits, Eating habits, etc). Users with high risk of and from the infection will be advised to take precautionary measures. Such data for positive cases will also help improve clinical care protocols by revealing co-morbidities, risk-factors and adverse drug interactions. 

The app has a verified self-reporting feature, where the user can check their risk of having the infection through a symptom tracker and schedule an appointment if necessary. Scheduling an appoinment securely and privately arranges for test results to be communicated back to the user. It seamlessly integrates with hospital protocols since results can be updated through either the app or the web portal.

### INFOMED.LIVE

Infomed allows officials to stay updated about the status of hospitals. Hospitals can be viewed individually or grouped by geographical area or other criteria. The total inventory, patient load/capacity, personnel availability can be seen. Hospitals can update this information regularly with ease, as well as coordinate patient test scheduling and result communication through the infomed or equally through the mobile app.

### GPS ANONYMIZATION ALGORITHM
Please refer to 
![Decentralized Computation of Density](https://github.com/Lifespark-Technologies/CoCo/blob/master/DCD.pdf)

## REFERENCES
1) Similarities between COVID-19 and Influenza. WHO-int. Mar 2020 [Online] Available: https://www.who.int/news-room/q-a-detail/q-a-similarities-and-differences-covid-19-and-influenza

2) Coronavirus and Acute Respiratory Diseases (COVID-19, SARS-Cov and MERS). March 2020 [Online]. 
Available:https://www.msdmanuals.com/professional/infectious-diseases/respiratory-viruses/coronaviruses-and-acute-respiratory-syndromes-covid-19,-mers,-and-sars

3) Impact of non-pharmaceutical interventions (NPIs) to reduce COVID-19 mortality and healthcare demand; Ferguson, Neil M and Laydon, Daniel and Nedjati-Gilani, Gemma and Imai, Natsuko and Ainslie, Kylie and Baguelin, Marc and Bhatia, Sangeeta and Boonyasiri, Adhiratha and Cucunub, Zulma and Cuomo-Dannenberg, Gina and others; Imperial College, London. DOI: https://doi. org/10.25561/77482

4) Estimated effectiveness of symptom and risk screening to prevent the spread of COVID-19; Gostic, Katelyn and Gomez, Ana CR and Mummah, Riley O and Kucharski, Adam J and Lloyd-Smith, James O; Elife; eLife Sciences Publications, Ltd; 2020

5) Quantifying dynamics of SARS-CoV-2 transmission suggests that epidemic control and avoidance is feasible through instantaneous digital contact tracing.
Available:https://github.com/BDI-pathogens/covid-19_instant_tracing/blob/master/Manuscript%20-%20Modelling%20instantaneous%20digital%20contact%20tracing.pdf

6) As Coronavirus Surveillance Escalates, Personal Privacy Plummets.
Available:https://www.nytimes.com/2020/03/23/technology/coronavirus-surveillance-tracking-privacy.html

7) Coronavirus privacy: Are South Korea's alerts too revealing?
   Available: https://www.bbc.com/news/world-asia-51733145

8) Contact Tracing Mobile Apps for COVID-19: Privacy Considerations and Related Trade-offs; Hyunghoon Cho and Daphne Ippolito and Yun William Yu; 2003.11511; 2020

9) Evaluating and Testing Persons for Coronavirus Disease 2019 (COVID-19) Mar 2020 [Online]. Available: https://www.cdc.gov/coronavirus/2019-ncov/hcp/clinical-criteria.html








ALL RIGHT RESERVED © 2020 Amey Desai
