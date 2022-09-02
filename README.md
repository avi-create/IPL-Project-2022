# IPL-Project-2022
Analyzing the IPL 2022 Auction data.

First of all will import all the libraries in the which is needed in the dataset.

![Capture1](https://user-images.githubusercontent.com/79398731/188058586-51568191-1b67-465d-845b-777994644cc0.PNG)

Now the dataset is successfully loaded and explore over dataset with HEAD function which will show the Top 5 rows of the dataset.

![Capture2](https://user-images.githubusercontent.com/79398731/188060265-4c8021f0-4c6e-4d45-bd78-9cf445e8fdbc.PNG)


Here we have different columns, we have different columns we have Unnamed column which is actually unnecessary for over analysis, so we see how to drop this column.

![Capture3](https://user-images.githubusercontent.com/79398731/188060459-acd6418e-ee61-4b84-babb-3b2f67008314.PNG)

We can see there are total 633 players that were the part of the auction and total 8 columns in my dataframe IPL.

![Capture4](https://user-images.githubusercontent.com/79398731/188061519-b2aea24f-8848-4357-93a1-0fa7b0a136b9.PNG)

This shows the number of columns in the dataset.

![Capture5](https://user-images.githubusercontent.com/79398731/188062318-7a5bb543-477a-4672-a51d-49e38c130d28.PNG)


I have used drop function here to drop Unnmaed column permanently from the dataset and we will check dataset again, dropped column is permanently removed from the dataset.

![Capture6](https://user-images.githubusercontent.com/79398731/188062580-c9b7c508-7695-4bf3-8810-18c5b1d6fa8e.PNG)

Lets see the total number of null values present in the dataset, there is null values in come columns the reason being those players were not picked in the IPL and hence there was no price associated.


![Capture7](https://user-images.githubusercontent.com/79398731/188063902-9a211372-f66e-44c5-881c-a678760cd0b9.PNG)

I have passed the 'Cost in $ (000)' column where we can see the NULL values.

![Capture8](https://user-images.githubusercontent.com/79398731/188064967-b11f75eb-62a4-4493-8a46-905725d80fe9.PNG)

The next thing is to pass 0 instead of NULL values where there are NULL values in the column.

![Capture9](https://user-images.githubusercontent.com/79398731/188065778-c5b0770d-2218-469b-a328-f69085b51dd0.PNG)

Now we will see the players which remain unsold in the 2021 squad column means we will check the rows with NULL values.


![Capture10](https://user-images.githubusercontent.com/79398731/188067052-e5716b23-1d5b-4242-8991-d579576177db.PNG)

We will replace NULL values with Not Participated in the column '2021 Squad' for the players who didnot participated in the 2021 Squad. Now we will check the NULL values in the dataset, and it will show that there are no null values in the dataset.

![Capture11](https://user-images.githubusercontent.com/79398731/188070615-2c337618-18c3-40e0-aaa0-5e96593fb478.PNG)


Here it will give the Unique values of the Team whose 'COST IN ₹ (CR.)' is greater than 0. Through this variable 'Teams' we will create the column Status where we will replace teams with Sold string. This means the teams having 'COST IN ₹ (CR.)' > 0 will be replaced with value Sold.


![Capture12](https://user-images.githubusercontent.com/79398731/188071440-b4d422b8-c16f-4fdc-9daf-0f2f67bda174.PNG)

Now we will remove duplicate records of the 'Players'.


![Capture13](https://user-images.githubusercontent.com/79398731/188072510-5d35587f-72a5-4c75-8916-05c1416e745e.PNG)

In this line of code we are finding how many types of players have participated.


![Capture14](https://user-images.githubusercontent.com/79398731/188073763-95a6460b-3bd1-4852-afcd-584031353263.PNG)

We have created a pie chart of the above table All-Rounders have 242, Bowler having value of 215 and so on.


![Capture15](https://user-images.githubusercontent.com/79398731/188077001-5806a378-2d26-4982-ba51-b45e26237d0f.PNG)

In this line of code it shows that how many number of players remain sold and unsold which will be shown by using Countplot 'Status' column.

# Total number of players bought by each team.

plt.figure(figsize=(20,10))
fig = sns.countplot(ipl[ipl['Team']!='Unsold']['Team'])
plt.xlabel('Team Names')
plt.ylabel('Number of Players')
plt.title('Players bought by each team', fontsize=12)
plt.xticks(rotation=70)
plt.plot()

for p in fig.patches:
    fig.annotate(format(p.get_height(), '.0f'),(p.get_x() + p.get_width()/2., p.get_height()), ha = 'center', va='center', xytext = (0,4), textcoords='offset points')

![Capture16](https://user-images.githubusercontent.com/79398731/188079448-5d221487-9a05-45cf-9dda-c2ac17100fbe.PNG)
![Capture17](https://user-images.githubusercontent.com/79398731/188079510-2e519244-3f53-4741-9044-554e1ea1f597.PNG)

In this we are showing total number of players bought by each team using Countplot and Team column and in the below section of the code for is defining the inner portion of the plot. Maximum team can purchase 24 Players in a team.


![Capture18](https://user-images.githubusercontent.com/79398731/188139856-fe56d5de-616b-4017-96b3-8fbc11778b94.PNG)

We are creating new column Retention and replacing values from Retention Column '2 Cr', '40 lakh', '20 lakh', '1 Cr', '75 lakh','50 lakh','30 lakh','1.5 Cr' with 'From Auction'
And replacing 'Draft Pick' with 0 from 'Base Price' column.
Now we are creating two more columns. First Column is 'Base_Price_unit' which will only units eg:- if there is value 20 Cr then the column will only contain Cr value.
Another column is 'base_price' it will only contain values eg:- if there is value 50 lakh then it will only contain 50.
Replace retained with zero in the base price column.


![Capture19](https://user-images.githubusercontent.com/79398731/188141116-ee217ff3-05aa-4483-ba26-ef5fecd3770d.PNG)

Total players bought and retained from each of the team


![Capture20](https://user-images.githubusercontent.com/79398731/188143096-2080bbd9-6f86-4018-8d0c-b4cb59484017.PNG)

It is displaying the players in each team based on different types of players. Here the TYPE is used in the hue because I want to show the players in each team based on the different types.


![Capture21](https://user-images.githubusercontent.com/79398731/188146175-a7c42dd1-c826-4f73-bda7-b593fce2a6a0.PNG)

Highest amount spend on a single player by each team


![Capture22](https://user-images.githubusercontent.com/79398731/188148877-13561382-3d8f-47dc-9669-2d6d8f8089e6.PNG)

Top 1 Player retained at maximum price. Ravindra Jadeja who was retained for 16 crores by Chennai Super Kings.


![Capture23](https://user-images.githubusercontent.com/79398731/188150330-05baa9fd-1dbd-4416-b60d-b4cc589676f8.PNG)

Top 5 Bowlers who are bought in COST IN ₹ (CR.). There is Deepak Chahar in 14 Crores and Shardul Thakur in 10.75 Crores and so on.


![Capture24](https://user-images.githubusercontent.com/79398731/188152135-84b45a0c-dc70-4c5c-a291-f59e4e1e68ac.PNG)

Now I want to see the players who were the part of the ipl last season but were not picked for this year's IPL.
