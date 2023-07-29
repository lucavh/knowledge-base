# Data Modelling

## Data Vault modelling

Data vault attempts to solve the problem of dealing with change in the environment by separating the business keys (hubs), that do not mutate as often, because they uniquely identify a business entity, and the associations between those business keys (links), from the descriptive attributes of those keys (satellites).

Pros
- Keeps track of history
- Agile

## Data Mesh

Data mesh is a decentralized organizational and technical approach in sharing, accessing and managing data for analytics and ML. Its objective is to create a sociotechnical approach that scales out getting value from data as the organization's complexity grows and as the use cases for data proliferate and the sources of data diversify. Essentially, it creates a responsible data-sharing model that is in step with organizational growth and continuous change. In our experience, interest in the application of data mesh has grown tremendously. The approach has inspired many organizations to embrace its adoption and technology providers to repurpose their existing technologies for a mesh deployment. Despite the great interest and growing experience in data mesh, its implementations face high cost of integration. Moreover, its adoption remains limited to sections of larger organizations and technology vendors are distracting the organizations from the hard socio aspects of data mesh — decentralized data ownership and a federated governance operating model.


https://blog.picnic.nl/q-a-picnic-data-engineering-series-4ba115491885