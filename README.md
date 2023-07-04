

# Project Title

Items Classification

# Description

Implement an unsupervised model to classify the items into several categories.
In this project, i will implement a clustering technique since we don't have any predefined labels for classification

### Phase1: Connection to the db & saving csv files for train and test
In this step i connected to the database and saved 2 files in a .csv format inside Data folder:  

*items.csv(50000 rows): for computation power purposes i had to select a chunk of data for training  
*items_test.csv(500 rows): for testing purposes

### Phase2: Data setup
Import the data as pandas dataframe and explore its characteristics

### Phase3: Feature selection & cleaning
In this step i dropped the features that does not have an impact on our clustering method( a lot of NULL values, ids, or creation date...)
i dropped also the rows that have negative "amount" or "taxAmont" value

### Phase4: Features preprocessing
In this section i applied on the selected features 2 types of preprocessing technique:  

*Encoding: we have to encode the categorical features into numeric so the model can interpret the columns content  
*Scaling: we scale the numeric into values between -1 and 1, we scale the columns in order to prevent the model from being biased 

### Phase5: Selection of optimum number of clusters(Elbow method)
In this section i have decided to use K-means model because its efficiency and scalability in clustering problems, k-means has also a good interpretability since it uses representation by the centroid.  
The prestep before training is to decide the number of classes to define, for that i used the Elbow method that involves fitting the k-means algorithm for diﬀerent values of
k and plotting the sum of squared distances between the instances and their respective cluster centroid against k.  

The number of clusters that corresponds to the "elbow" point on the plot,where the within-cluster sum of squares(wcss) begins to decrease at a slower rate, is considered the correct number of clusters, which is 4 in this case.

### Phase6: Model training
In this step we fit our preprocessed data and predict the results for clusters then we persist the model in the folder Models so we can use used in our prediction function
For a better visualization of our classes, i plotted a 2D chart using "amount" and "taxRate" columns: in my plot i changed the scale of X so we can see better the main classes except the cluster2 because it's related to only few data points(around 20 records)

### Phase7: Exploring the clusters
This is the most challenging part because it needs a good understanding of the business to assign every cluster to meaningful class.  
By exploring the result i noticed a relation between the taxRate and the clusters, i started to dig deeper and after online research i fount that there is multiple classes of taxes that can give us hints about the type of the product the classes are as below(i picked the french version):

*Le taux normal de la TVA est fixé à 20 %, pour la majorité des ventes de biens et des prestations de services : il s'applique à tous les produits ou services pour lesquels aucun autre taux n'est expressément prévu.  
*Le taux réduit de 10 % est notamment applicable aux produits agricoles non transformés, au bois de chauffage, aux travaux d'amélioration du logement qui ne bénéficient pas du taux de 5,5%, à certaines prestations de logement et de camping, aux foires et salons, jeux et manèges forains, aux droits d'entrée des musées, zoo, monuments, aux transports de voyageurs, au traitement des déchets, à la restauration.  
*Le taux réduit de 5,5 % concerne l'essentiel des produits alimentaires, les produits de protection hygiénique féminine, équipements et services pour handicapés, livres sur tout support, abonnements gaz et électricité, fourniture de chaleur issue d’énergies renouvelables, fourniture de repas dans les cantines scolaires, billeterie de spectacle vivant et de cinéma, certaines importations et livraisons d'œuvres d'art, travaux d’amélioration de la qualité énergétique des logements, logements sociaux ou d'urgence, accession à la propriété.  


Fro cluster number2 i assigned it to particular_tax_rate because it does not belong to any of the above classes.


# Getting Started
To run the prediction function you only need to extract a csv file with the number of rows that you wish and feed it as dataframe

# Dependencies

Install the libraries included in requirements.txt

# Authors

Mohamed Amine Filali 

