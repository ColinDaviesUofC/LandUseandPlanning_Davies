# LandUseandPlanning_Davies
**Data_Davies **

Processed by: Colin Davies
              colin.davies@ucalgary.ca 
Instructor: Dr. Victoria Fast 
	          victoria.fast@ucalgary.ca 
           
University of Calgary 
2500 University Dr NW, Calgary, AB T2N 1N4

Data processed between 2024/11/05 and 2024/11/17

Geographic location: Calgary, Alberta, Canada
 
The data contains neighborhood-level metrics for Calgary, including median single-family lot size, housing density, building footprint coverage, median Floor Area Ratio, and an entropy index for land cover diversity, stored in a .csv file. Datasets were collected from The City of Calgary’s Open Data Portal. 

https://data.calgary.ca/

https://data.calgary.ca/stories/s/Open-Calgary-Terms-of-Use/u45n-7awa 

CSV file was created on 2024/11/25 

Calculations were performed in Excel and ArcGIS Pro

Median family lot size was calculated from the Current Year Property Assessments (Parcel) shapefile. Using the ‘Summarize Statistics’ tool, the median lot size was calculated for each residential neighbourhood. The median lot size is displayed in square meters. 

Housing density was calculated from the Community District Boundaries and Parcel Address shapefiles. Using ‘Calculate Geography’, the size of the communities was calculated in square kilometers. Then, the count of houses was found using the ‘Summarize Within’ tool. Finally, a field was added to the Community District Boundaries table where the ‘Calculate Field’ tool was used to divide housing count by community area. Housing density is displayed in housing units per square kilometer. 

Building footprint was calculated from the Community District Boundaries and Buildings shapefiles. Using ‘Calculate Geography’, the size of the communities was calculated in square kilometers. Then, the area of house footprints was calculated in square kilometers using the ‘Summarize Within’ tool. Finally, a field was added to the Community District Boundaries table where the ‘Calculate Field’ tool was used to divide housing area by community area. Building coverage is displayed as a ratio. 

Median Floor-Area-Ratio (FAR) was calculated from the Community District Boundaries, Buildings, Current Year Property Assessments (Parcel), and 3D Buildings – Citywide (LiDAR) shapefiles. The floor area of the buildings and lots were determined using ‘Calculate Geometry’. A spatial join was conducted to link the Parcels, Buildings, and LiDAR files. This joined layer was then exported to Excel using the ‘Table to Excel’ tool. In Excel the FAR calculations were performed. The FAR formula can be seen in Equation 1. The height of the building was calculated from the LiDAR data by subtracting max building height from property height. This number was then divided by 3m (average storey height), to determine the number of floors. The FAR was then calculated and imported back into ArcGIS Pro using the ‘Excel to Table’ tool and joined to the Community District Boundaries layer. Finally, the FAR median by community was calculated using ‘Summarize Statistics’. 

				Floor Area Ratio=  ((n × Building Floor Area))/(Total Lot Area)			[1] 
      
            where:
              "n = number of floors" 

Entropy Index was calculated from the Community District Boundaries and Land Use Districts shapefiles. Using ‘Calculate Geography’, the size of the communities was calculated in square kilometers. Next, the area of land use districts was calculated using the ‘Summarize Within’ tool. The layers were exported to Excel using the ‘Table to Excel’ tool. The Entropy Index was calculated using the formula which can be seen in Equation 2. The results were imported back into ArcGIS Pro using the ‘Excel to Table’ tool and joined to the Community District Boundaries layer. 

				Entropy= -∑_(i=1)^k▒(P_i  ln⁡〖(P_i)〗)/ln⁡k 					[2]
    
			where:
				k = number of land uses
				P_i = proportion of building area for the use of i

Variable Labels and Descriptions: 

comm_code: community code (three-digit identifier) 

name: community name

sector: quadrant of city that community is located in 

srg: denotes whether community is established, developing, or completed 

comm_struc: community construction date 

area: area of community (square kilometers) 

FAR_Median: median floor-area-ratio

Entropy: entropy-based land-use mix index

Buildings_Ratio: ratio of area of buildings to total community area 

Density_Housing: houses per square kilometer 

Median_Lotsize: median lot size of community (square meters)


References: 

City of Calgary. (2020). Municipal Development Plan (MDP) – 2020. The City of Calgary. https://www.calgary.ca/planning/municipal-development-plan.html

Habibi, S., & Asadi, N. (2011). Causes, results and methods of controlling urban sprawl. Procedia Engineering, 21, 133–141. https://doi.org/10.1016/j.proeng.2011.11.1996 

Im, H. N., & Choi, C. G. (2018). The hidden side of the entropy-based land-use mix index: Clarifying the relationship between pedestrian volume and land-use mix. Urban Studies, 56(9), 1865–1881. https://doi.org/10.1177/0042098018763319 

Jaeger, J. A. G., Bertiller, R., Schwick, C., & Kienast, F. (2010). Suitability criteria for measures of urban sprawl. Ecological Indicators, 10(2), 397–406. https://doi.org/10.1016/j.ecolind.2009.07.007 

Lowry, J. H., & Lowry, M. B. (2014). Comparing spatial metrics that quantify urban form. Computers, Environment and Urban Systems, 44, 59–67. https://doi.org/10.1016/j.compenvurbsys.2013.11.005 

Manaugh, K., & Kreider, T. (2013). What is mixed use? presenting an interaction method for measuring land use mix. Journal of Transport and Land Use, 6(1), 63–72. https://doi.org/10.5198/jtlu.v6i1.291

Steurer, M., & Bayr, C. (2020). Measuring urban sprawl using Land Use Data. Land Use Policy, 97, 104799. https://doi.org/10.1016/j.landusepol.2020.104799 

Contains information licensed under the Open Government Licence – City of Calgary
