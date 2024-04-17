# world-energy-consumption-analysis

<b>Data ethics and bias considerations:</b>

The primary dataset leveraged for this project is sourced from: https://www.kaggle.com/datasets/pralabhpoudel/world-energy-consumption. The data is derived from multiple sources, and the dataset has been updated as new data has become available. In an attempt to have a tenable scope for the project and avoid bias as much as possible, we decided to limit our analysis to the world's 25 most populous countires based on information available from: https://www.worldometers.info/world-population/population-by-country/. The population data is an aggregation based on information collected by the U.N., which is publicly available at: https://population.un.org/wpp/. The types of energy a country consumed, in what year consumption of that energy began, annual gross domestic product, and geographic location had no bearing on the determination of a coutry's inclusion in the project. Further, from a data ethics standpoint, the World Energy Consumption dataset was selected because it is comprised of publicly available data, and the code used to ingest + process the data is provided by the authors. This combination ensures that users of the dataset have full visibility into how the data is being handled from beginning to end. 

<b>Running data and analysis:</b>

The data that powers our analysis is housed within a PostgreSQL database that can be hosted locally:
<ul>
  <li>The ‘global-energy-cons-data.csv’ file located in the repo is an abridged version of the larger dataset.</li>
  <li>The primary .ipynb file within the repo reads in the CSV and performs necessary data hygiene functions, and then writes the updated dataset to the ‘postgres_table.csv' file. This will be written to your working directory.</li>
  <li>The ‘energy_data_schema.sql’ file within the repo contains the SQL code needed to create a table within your PostgreSQL database to store the data.</li>
    <ul>
      <li>Within your PGAdmin interface, create a new database. Once the database is created, right click and open the query tool. Copy the contents of the 'energy_data_schema.sql' file into the query tool and run the query to create a table within your database. By default, the table will be named 'energy_data', but you can rename the table as you see fit</li>
    </ul>
  <li>The ‘postgres_table.csv’ file can be used to populate the table once it is created</li>
  <li>Once the PostgreSQL database is configured, the primary ipynb file within the repo contains logic for reading the database via SQLAlchemy.</li>
</ul>
