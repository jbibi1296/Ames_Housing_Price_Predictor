# Project 2: Ames, Iowa Kaggle Competition

## Contents

[Problem Statement](#Problem-Statment)

[Executive Summary](#Executive-Summary)

[Data Dictionary](#Data-Dictionary)


# Problem Statement

We are trying to make a price prediction template that can accurately predict the price of a house when given it's features.

# Executive Summary

We were approached by Zillow with a task of building a price-prediction template. The idea is to start with just Ames, IA and eventually we would bring it to the rest of the world. Zillow gave us 2 datasets of all houses in the city of Ames, Iowa with multiple columns that describe almost all aspects of the property. the 1st dataset had a column for price, and the 2nd did not. We are supposed to create a model that we can put the 2nd dataset into, and it could predict the prices for each house.Now that we have our task we can work on solving it.

We imported our data and checked the data to see if there are any missing values, incorrect data types, or values that we would need to change in order to correctly process the data. We found that there were many missing values, and many columns that we would need to change its values to properly run them through our model. We put zeros in place of the missing values and put a ranking system in place for all columns that had ordinal values but were not numbered. At this point, all we had left to do was to fix the columns that were not numbers and also not ranked. What we did was we created new columns for each feature that would show up and placed either a 1 or a 0 in the cell depending on whether the house had that feature or not. This practice is called One-Hot-Encoding and it is very common practice. Lastly, we re-analyzed our data to make sure that it is ready to move to the next step.

Now that we had all of our data properly formatted, we created new columns. We found that there were many columns that we felt would be better if it were to be summed together. We also created new columns for houses that were built in the 21st century, and for houses that we classified as 'Mansions'. Creating new columns can be a real hit or miss and we hoped that these would help us with our model.

Moving on, we wanted to visualize all of our data including our new columns. We performed a report to see if our data is too repetitive, created histograms to look at the distribution of each column, and looked at a few heatmaps to see how each column correlated with each other and how they correlated with the 'SalePrice' column. We were now able to pick and choose our columns so we chose all columns that had a .54 absolute correlation or higher(Between -1:-.54 and .54:1). We looked at our columns again and removed any columns that were colinear with one of our chosen columns. Now we have our features for our model.

We built 15 different models to test out different combinations of estimators, Scalers, Transformers, and whether or not to create Polynomial Features. We split the data into a training and testing set so we can evaluate how well our model predicted the price of those in our testing set. Each of the 15 models gave us different CV Scores, Root mean square error scores, and r^2 scores.

We then created a dictionary showing how each model did so we can compare the scores to each other.

Lastly, we chose the best model that best fit the columns to the Price.


# Data Dictionary

Order (Discrete): Observation number

PID (Nominal): Parcel identification number  - can be used with city web site for parcel review. 

MS SubClass (Nominal): Identifies the type of dwelling involved in the sale.	

       020	1-STORY 1946 & NEWER ALL STYLES
       030	1-STORY 1945 & OLDER
       040	1-STORY W/FINISHED ATTIC ALL AGES
       045	1-1/2 STORY - UNFINISHED ALL AGES
       050	1-1/2 STORY FINISHED ALL AGES
       060	2-STORY 1946 & NEWER
       070	2-STORY 1945 & OLDER
       075	2-1/2 STORY ALL AGES
       080	SPLIT OR MULTI-LEVEL
       085	SPLIT FOYER
       090	DUPLEX - ALL STYLES AND AGES
       120	1-STORY PUD (Planned Unit Development) - 1946 & NEWER
       150	1-1/2 STORY PUD - ALL AGES
       160	2-STORY PUD - 1946 & NEWER
       180	PUD - MULTILEVEL - INCL SPLIT LEV/FOYER
       190	2 FAMILY CONVERSION - ALL STYLES AND AGES

MS Zoning (Nominal): Identifies the general zoning classification of the sale.
		
       A	Agriculture
       C	Commercial
       FV	Floating Village Residential
       I	Industrial
       RH	Residential High Density
       RL	Residential Low Density
       RP	Residential Low Density Park 
       RM	Residential Medium Density
	
Lot Frontage (Continuous): Linear feet of street connected to property

Lot Area (Continuous): Lot size in square feet

Street (Nominal): Type of road access to property

       Grvl	Gravel	
       Pave	Paved
       	
Alley (Nominal): Type of alley access to property

       Grvl	Gravel
       Pave	Paved
       NA 	No alley access
		
Lot Shape (Ordinal): General shape of property

       Reg	Regular	
       IR1	Slightly irregular
       IR2	Moderately Irregular
       IR3	Irregular
       
Land Contour (Nominal): Flatness of the property

       Lvl	Near Flat/Level	
       Bnk	Banked - Quick and significant rise from street grade to building
       HLS	Hillside - Significant slope from side to side
       Low	Depression
		
Utilities (Ordinal): Type of utilities available
		
       AllPub	All public Utilities (E,G,W,& S)	
       NoSewr	Electricity, Gas, and Water (Septic Tank)
       NoSeWa	Electricity and Gas Only
       ELO	Electricity only	
	
Lot Config (Nominal): Lot configuration

       Inside	Inside lot
       Corner	Corner lot
       CulDSac	Cul-de-sac
       FR2	Frontage on 2 sides of property
       FR3	Frontage on 3 sides of property
	
Land Slope (Ordinal): Slope of property
		
       Gtl	Gentle slope
       Mod	Moderate Slope	
       Sev	Severe Slope
	
Neighborhood (Nominal): Physical locations within Ames city limits (map available)

       Blmngtn	Bloomington Heights
       Blueste	Bluestem
       BrDale	Briardale
       BrkSide	Brookside
       ClearCr	Clear Creek
       CollgCr	College Creek
       Crawfor	Crawford
       Edwards	Edwards
       Gilbert	Gilbert
       Greens	Greens
       GrnHill	Green Hills
       IDOTRR	Iowa DOT and Rail Road
       Landmrk	Landmark
       MeadowV	Meadow Village
       Mitchel	Mitchell
       Names	North Ames
       NoRidge	Northridge
       NPkVill	Northpark Villa
       NridgHt	Northridge Heights
       NWAmes	Northwest Ames
       OldTown	Old Town
       SWISU	South & West of Iowa State University
       Sawyer	Sawyer
       SawyerW	Sawyer West
       Somerst	Somerset
       StoneBr	Stone Brook
       Timber	Timberland
       Veenker	Veenker
			
Condition 1 (Nominal): Proximity to various conditions
	
       Artery	Adjacent to arterial street
       Feedr	Adjacent to feeder street	
       Norm	Normal	
       RRNn	Within 200' of North-South Railroad
       RRAn	Adjacent to North-South Railroad
       PosN	Near positive off-site feature--park, greenbelt, etc.
       PosA	Adjacent to postive off-site feature
       RRNe	Within 200' of East-West Railroad
       RRAe	Adjacent to East-West Railroad
	
Condition 2 (Nominal): Proximity to various conditions (if more than one is present)
		
       Artery	Adjacent to arterial street
       Feedr	Adjacent to feeder street	
       Norm	Normal	
       RRNn	Within 200' of North-South Railroad
       RRAn	Adjacent to North-South Railroad
       PosN	Near positive off-site feature--park, greenbelt, etc.
       PosA	Adjacent to postive off-site feature
       RRNe	Within 200' of East-West Railroad
       RRAe	Adjacent to East-West Railroad
	
Bldg Type (Nominal): Type of dwelling
		
       1Fam	Single-family Detached	
       2FmCon	Two-family Conversion; originally built as one-family dwelling
       Duplx	Duplex
       TwnhsE	Townhouse End Unit
       TwnhsI	Townhouse Inside Unit
	
House Style (Nominal): Style of dwelling
	
       1Story	One story
       1.5Fin	One and one-half story: 2nd level finished
       1.5Unf	One and one-half story: 2nd level unfinished
       2Story	Two story
       2.5Fin	Two and one-half story: 2nd level finished
       2.5Unf	Two and one-half story: 2nd level unfinished
       SFoyer	Split Foyer
       SLvl	Split Level
	
Overall Qual (Ordinal): Rates the overall material and finish of the house

       10	Very Excellent
       9	Excellent
       8	Very Good
       7	Good
       6	Above Average
       5	Average
       4	Below Average
       3	Fair
       2	Poor
       1	Very Poor
	
Overall Cond (Ordinal): Rates the overall condition of the house

       10	Very Excellent
       9	Excellent
       8	Very Good
       7	Good
       6	Above Average	
       5	Average
       4	Below Average	
       3	Fair
       2	Poor
       1	Very Poor
		
Year Built (Discrete): Original construction date

Year Remod/Add (Discrete): Remodel date (same as construction date if no remodeling or additions)

Roof Style (Nominal): Type of roof

       Flat	Flat
       Gable	Gable
       Gambrel	Gabrel (Barn)
       Hip	Hip
       Mansard	Mansard
       Shed	Shed
		
Roof Matl (Nominal): Roof material

       ClyTile	Clay or Tile
       CompShg	Standard (Composite) Shingle
       Membran	Membrane
       Metal	Metal
       Roll	Roll
       Tar&Grv	Gravel & Tar
       WdShake	Wood Shakes
       WdShngl	Wood Shingles
		
Exterior 1 (Nominal): Exterior covering on house

       AsbShng	Asbestos Shingles
       AsphShn	Asphalt Shingles
       BrkComm	Brick Common
       BrkFace	Brick Face
       CBlock	Cinder Block
       CemntBd	Cement Board
       HdBoard	Hard Board
       ImStucc	Imitation Stucco
       MetalSd	Metal Siding
       Other	Other
       Plywood	Plywood
       PreCast	PreCast	
       Stone	Stone
       Stucco	Stucco
       VinylSd	Vinyl Siding
       Wd Sdng	Wood Siding
       WdShing	Wood Shingles
	
Exterior 2 (Nominal): Exterior covering on house (if more than one material)

       AsbShng	Asbestos Shingles
       AsphShn	Asphalt Shingles
       BrkComm	Brick Common
       BrkFace	Brick Face
       CBlock	Cinder Block
       CemntBd	Cement Board
       HdBoard	Hard Board
       ImStucc	Imitation Stucco
       MetalSd	Metal Siding
       Other	Other
       Plywood	Plywood
       PreCast	PreCast
       Stone	Stone
       Stucco	Stucco
       VinylSd	Vinyl Siding
       Wd Sdng	Wood Siding
       WdShing	Wood Shingles
	
Mas Vnr Type (Nominal): Masonry veneer type

       BrkCmn	Brick Common
       BrkFace	Brick Face
       CBlock	Cinder Block
       None	None
       Stone	Stone
	
Mas Vnr Area (Continuous): Masonry veneer area in square feet

Exter Qual (Ordinal): Evaluates the quality of the material on the exterior 
		
       Ex	Excellent
       Gd	Good
       TA	Average/Typical
       Fa	Fair
       Po	Poor
		
Exter Cond (Ordinal): Evaluates the present condition of the material on the exterior
		
       Ex	Excellent
       Gd	Good
       TA	Average/Typical
       Fa	Fair
       Po	Poor
		
Foundation (Nominal): Type of foundation
		
       BrkTil	Brick & Tile
       CBlock	Cinder Block
       PConc	Poured Contrete	
       Slab	Slab
       Stone	Stone
       Wood	Wood
		
Bsmt Qual (Ordinal): Evaluates the height of the basement

       Ex	Excellent (100+ inches)	
       Gd	Good (90-99 inches)
       TA	Typical (80-89 inches)
       Fa	Fair (70-79 inches)
       Po	Poor (<70 inches
       NA	No Basement
		
Bsmt Cond (Ordinal): Evaluates the general condition of the basement

       Ex	Excellent
       Gd	Good
       TA	Typical - slight dampness allowed
       Fa	Fair - dampness or some cracking or settling
       Po	Poor - Severe cracking, settling, or wetness
       NA	No Basement
	
Bsmt Exposure	(Ordinal): Refers to walkout or garden level walls

       Gd	Good Exposure
       Av	Average Exposure (split levels or foyers typically score average or above)	
       Mn	Mimimum Exposure
       No	No Exposure
       NA	No Basement
	
BsmtFin Type 1	(Ordinal): Rating of basement finished area

       GLQ	Good Living Quarters
       ALQ	Average Living Quarters
       BLQ	Below Average Living Quarters	
       Rec	Average Rec Room
       LwQ	Low Quality
       Unf	Unfinshed
       NA	No Basement
		
BsmtFin SF 1 (Continuous): Type 1 finished square feet

BsmtFinType 2	(Ordinal): Rating of basement finished area (if multiple types)

       GLQ	Good Living Quarters
       ALQ	Average Living Quarters
       BLQ	Below Average Living Quarters	
       Rec	Average Rec Room
       LwQ	Low Quality
       Unf	Unfinshed
       NA	No Basement

BsmtFin SF 2 (Continuous): Type 2 finished square feet

Bsmt Unf SF (Continuous): Unfinished square feet of basement area

Total Bsmt SF (Continuous): Total square feet of basement area

Heating	(Nominal): Type of heating
		
       Floor	Floor Furnace
       GasA	Gas forced warm air furnace
       GasW	Gas hot water or steam heat
       Grav	Gravity furnace	
       OthW	Hot water or steam heat other than gas
       Wall	Wall furnace
		
HeatingQC (Ordinal): Heating quality and condition

       Ex	Excellent
       Gd	Good
       TA	Average/Typical
       Fa	Fair
       Po	Poor
		
Central Air (Nominal): Central air conditioning

       N	No
       Y	Yes
		
Electrical (Ordinal): Electrical system

       SBrkr	Standard Circuit Breakers & Romex
       FuseA	Fuse Box over 60 AMP and all Romex wiring (Average)	
       FuseF	60 AMP Fuse Box and mostly Romex wiring (Fair)
       FuseP	60 AMP Fuse Box and mostly knob & tube wiring (poor)
       Mix	Mixed
		
1st Flr SF (Continuous): First Floor square feet
 
2nd Flr SF (Continuous)	: Second floor square feet

Low Qual Fin SF (Continuous): Low quality finished square feet (all floors)

Gr Liv Area (Continuous): Above grade (ground) living area square feet

Bsmt Full Bath (Discrete): Basement full bathrooms

Bsmt Half Bath (Discrete): Basement half bathrooms

Full Bath (Discrete): Full bathrooms above grade

Half Bath (Discrete): Half baths above grade

Bedroom (Discrete): Bedrooms above grade (does NOT include basement bedrooms)

Kitchen (Discrete): Kitchens above grade

KitchenQual (Ordinal): Kitchen quality

       Ex	Excellent
       Gd	Good
       TA	Typical/Average
       Fa	Fair
       Po	Poor
       	
TotRmsAbvGrd	(Discrete): Total rooms above grade (does not include bathrooms)

Functional (Ordinal): Home functionality (Assume typical unless deductions are warranted)

       Typ	Typical Functionality
       Min1	Minor Deductions 1
       Min2	Minor Deductions 2
       Mod	Moderate Deductions
       Maj1	Major Deductions 1
       Maj2	Major Deductions 2
       Sev	Severely Damaged
       Sal	Salvage only
		
Fireplaces (Discrete): Number of fireplaces

FireplaceQu (Ordinal): Fireplace quality

       Ex	Excellent - Exceptional Masonry Fireplace
       Gd	Good - Masonry Fireplace in main level
       TA	Average - Prefabricated Fireplace in main living area or Masonry Fireplace in basement
       Fa	Fair - Prefabricated Fireplace in basement
       Po	Poor - Ben Franklin Stove
       NA	No Fireplace
		
Garage Type (Nominal): Garage location
		
       2Types	More than one type of garage
       Attchd	Attached to home
       Basment	Basement Garage
       BuiltIn	Built-In (Garage part of house - typically has room above garage)
       CarPort	Car Port
       Detchd	Detached from home
       NA	No Garage
		
Garage Yr Blt (Discrete): Year garage was built
		
Garage Finish (Ordinal)	: Interior finish of the garage

       Fin	Finished
       RFn	Rough Finished	
       Unf	Unfinished
       NA	No Garage
		
Garage Cars (Discrete): Size of garage in car capacity

Garage Area (Continuous): Size of garage in square feet

Garage Qual (Ordinal): Garage quality

       Ex	Excellent
       Gd	Good
       TA	Typical/Average
       Fa	Fair
       Po	Poor
       NA	No Garage
		
Garage Cond (Ordinal): Garage condition

       Ex	Excellent
       Gd	Good
       TA	Typical/Average
       Fa	Fair
       Po	Poor
       NA	No Garage
		
Paved Drive (Ordinal): Paved driveway

       Y	Paved 
       P	Partial Pavement
       N	Dirt/Gravel
		
Wood Deck SF (Continuous): Wood deck area in square feet

Open Porch SF (Continuous): Open porch area in square feet

Enclosed Porch (Continuous): Enclosed porch area in square feet

3-Ssn Porch (Continuous): Three season porch area in square feet

Screen Porch (Continuous): Screen porch area in square feet

Pool Area (Continuous): Pool area in square feet

Pool QC (Ordinal): Pool quality
		
       Ex	Excellent
       Gd	Good
       TA	Average/Typical
       Fa	Fair
       NA	No Pool
		
Fence (Ordinal): Fence quality
		
       GdPrv	Good Privacy
       MnPrv	Minimum Privacy
       GdWo	Good Wood
       MnWw	Minimum Wood/Wire
       NA	No Fence
	
Misc Feature (Nominal): Miscellaneous feature not covered in other categories
		
       Elev	Elevator
       Gar2	2nd Garage (if not described in garage section)
       Othr	Other
       Shed	Shed (over 100 SF)
       TenC	Tennis Court
       NA	None
		
Misc Val (Continuous): Value of miscellaneous feature

Mo Sold (Discrete): Month Sold (MM)

Yr Sold (Discrete): Year Sold (YYYY)

Sale Type (Nominal): Type of sale
		
       WD 	Warranty Deed - Conventional
       CWD	Warranty Deed - Cash
       VWD	Warranty Deed - VA Loan
       New	Home just constructed and sold
       COD	Court Officer Deed/Estate
       Con	Contract 15\% Down payment regular terms
       ConLw	Contract Low Down payment and low interest
       ConLI	Contract Low Interest
       ConLD	Contract Low Down
       Oth	Other
		
Sale Condition (Nominal): Condition of sale

       Normal	Normal Sale
       Abnorml	Abnormal Sale -  trade, foreclosure, short sale
       AdjLand	Adjoining Land Purchase
       Alloca	Allocation - two linked properties with separate deeds, typically condo with a garage unit	
       Family	Sale between family members
       Partial	Home was not completed when last assessed (associated with New Homes)
		
SalePrice (Continuous): Sale price 

# Conclusion

After evaluating all of our models, we have a chart (below) that we can view our scores and choose the model that best fits our data.

<div>
<table border="1" class="dataframe">
  <thead>
    <tr style="text-align: right;">
      <th></th>
      <th>Test RMSE</th>
      <th>Train RMSE</th>
      <th>Train RMSE % more</th>
      <th>CV Score</th>
      <th>Test r2 Score</th>
      <th>Train r2 Score</th>
      <th>Best Parameters</th>
      <th>Features</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <th>Standard Scaler, Polynomial Features and Ridge Model</th>
      <td>21724.8</td>
      <td>22544.5</td>
      <td>-3.64% more</td>
      <td>0.895614</td>
      <td>0.912015</td>
      <td>0.913025</td>
      <td>{'poly__degree': 2}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler, Polynomial Features and Lasso Model</th>
      <td>23118.8</td>
      <td>22103.3</td>
      <td>4.59% more</td>
      <td>0.892348</td>
      <td>0.911082</td>
      <td>0.911714</td>
      <td>{'poly__degree': 3}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler, Polynomial Features and Linear Regression</th>
      <td>23841.3</td>
      <td>21812.6</td>
      <td>9.3% more</td>
      <td>0.897592</td>
      <td>0.919221</td>
      <td>0.916851</td>
      <td>{'poly__degree': 2}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler, Polynomial Features and Elastic Net Model</th>
      <td>24091.8</td>
      <td>21721.4</td>
      <td>10.91% more</td>
      <td>0.874178</td>
      <td>0.903158</td>
      <td>0.917513</td>
      <td>{'elast__l1_ratio': 1.0, 'poly__degree': 3}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Polynomial Features, Power Transform and Linear Regression</th>
      <td>24797.4</td>
      <td>23114.7</td>
      <td>7.28% more</td>
      <td>0.899088</td>
      <td>0.893056</td>
      <td>0.90533</td>
      <td>{'poly__degree': 2}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler, Polynomial Features, Power Transform and Ridge Model</th>
      <td>24808.6</td>
      <td>24461.3</td>
      <td>1.42% more</td>
      <td>0.714808</td>
      <td>0.893717</td>
      <td>0.891523</td>
      <td>{'poly__degree': 4}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Polynomial Features, Power Transform and Elastic Net Model</th>
      <td>26411.9</td>
      <td>28535.3</td>
      <td>-7.44% more</td>
      <td>0.787732</td>
      <td>0.888033</td>
      <td>0.848172</td>
      <td>{'elast__l1_ratio': 1.0, 'poly__degree': 3}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler, Polynomial Features, Power Transform and Lasso Model</th>
      <td>27791.6</td>
      <td>28133.6</td>
      <td>-1.22% more</td>
      <td>0.84973</td>
      <td>0.846091</td>
      <td>0.850503</td>
      <td>{'poly__degree': 3}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler, Polynomial Features, Power Transform and Linear Regression</th>
      <td>28028.7</td>
      <td>23375.5</td>
      <td>19.91% more</td>
      <td>0.872359</td>
      <td>0.863291</td>
      <td>0.904843</td>
      <td>{'poly__degree': 2}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler and Lasso Model</th>
      <td>28377.8</td>
      <td>35084.4</td>
      <td>-19.12% more</td>
      <td>0.79853</td>
      <td>0.812226</td>
      <td>0.766849</td>
      <td>{}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Polynomial Features, Power Transform and Ridge Model</th>
      <td>29811.4</td>
      <td>23286</td>
      <td>28.02% more</td>
      <td>0.877482</td>
      <td>0.834679</td>
      <td>0.90376</td>
      <td>{'poly__degree': 4}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Polynomial Features, Power Transform and Lasso Model</th>
      <td>30765.5</td>
      <td>30931.7</td>
      <td>-0.54% more</td>
      <td>0.802162</td>
      <td>0.816268</td>
      <td>0.812445</td>
      <td>{'poly__degree': 3}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler and Ridge Model</th>
      <td>33897.5</td>
      <td>33885.9</td>
      <td>0.03% more</td>
      <td>0.80274</td>
      <td>0.768044</td>
      <td>0.766257</td>
      <td>{}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler and Elastic Net Model</th>
      <td>34434.4</td>
      <td>33651.9</td>
      <td>2.33% more</td>
      <td>0.805662</td>
      <td>0.773639</td>
      <td>0.781897</td>
      <td>{'elast__l1_ratio': 1.0}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler, Polynomial Features, Power Transform and Elastic Net Model</th>
      <td>34671</td>
      <td>26883.6</td>
      <td>28.97% more</td>
      <td>0.833354</td>
      <td>0.805055</td>
      <td>0.867898</td>
      <td>{'elast__l1_ratio': 1.0, 'poly__degree': 3}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Linear Regression</th>
      <td>34685.3</td>
      <td>33599</td>
      <td>3.23% more</td>
      <td>0.801722</td>
      <td>0.774957</td>
      <td>0.774882</td>
      <td>{}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Standard Scaler and Linear Regression</th>
      <td>48733.1</td>
      <td>30289.5</td>
      <td>60.89% more</td>
      <td>0.844984</td>
      <td>0.646606</td>
      <td>0.824176</td>
      <td>{}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Lasso Model</th>
      <td>75776.4</td>
      <td>76828.9</td>
      <td>-1.37% more</td>
      <td>0.0550821</td>
      <td>-13.0559</td>
      <td>-13.3914</td>
      <td>{}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
    <tr>
      <th>Ridge Model</th>
      <td>1.18786e+08</td>
      <td>1.18833e+08</td>
      <td>-0.04% more</td>
      <td>-142292</td>
      <td>0.00014466</td>
      <td>0.000310264</td>
      <td>{}</td>
      <td>[Quals, SF_Sum, Gr Liv Area, Garage Area, Full...</td>
    </tr>
  </tbody>
</table>
        
We see from here that the Standard Scaler, Polynomial Features and Ridge Model (Model #9 in the Code) was the model with the Lowest Test Root Mean Square Error Score. It also has a great CV Score, Testing R^2 Score and Training R^2 Score!

This is the model that we are choosing to use for our Price Predictor for Zillow.
