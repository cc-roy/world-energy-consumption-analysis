# world-energy-consumption-analysis

<h2>Data ethics and bias considerations:</h2>

The primary dataset leveraged for this project is sourced from: https://www.kaggle.com/datasets/pralabhpoudel/world-energy-consumption. The data is derived from multiple sources, and the dataset has been updated as new data has become available. In an attempt to have a tenable scope for the project and avoid bias as much as possible, we decided to limit our analysis to the world's 25 most populous countries based on information available from: https://www.worldometers.info/world-population/population-by-country/. The population data is an aggregation based on information collected by the U.N., which is publicly available at: https://population.un.org/wpp/. The types of energy a country consumed, in what year consumption of that energy began, annual gross domestic product, and geographic location had no bearing on the determination of a country's inclusion in the project. Further, from a data ethics standpoint, the World Energy Consumption dataset was selected because it is comprised of publicly available data, and the code used to ingest + process the data is provided by the authors. This combination ensures that users of the dataset have full visibility into how the data is being handled from beginning to end. 

<h2>Running data and analysis:</h2>

The data that powers our analysis is housed within a PostgreSQL database that can be hosted locally:
<ul>
  <li>The ‘global-energy-cons-data.csv’ file located in the repo is an abridged version of the larger dataset.</li>
  <li>The primary .ipynb file within the repo reads in the CSV and performs necessary data hygiene functions, and then writes the updated dataset to the ‘postgres_table.csv' file. This will be written to your working directory.</li>
  <li>The ‘energy_data_schema.sql’ file within the repo contains the SQL code needed to create a table within your PostgreSQL database to store the data.</li>
    <ul>
      <li>Within your PGAdmin interface, create a new database. Once the database is created, right click and open the query tool. Copy the contents of the 'energy_data_schema.sql' file into the query tool and run the query to create a table within your database. By default, the table will be named 'energy_data', but you can rename the table as you see fit.</li>
    </ul>
  <li>The ‘postgres_table.csv’ file can be used to populate the table once it is created.</li>
    <ul>
      <li>Within your PGAdmin interface, right click on the table and click import/export data. Within the new dialogue box, select the 'postgres_table.csv' file from your directory, select UTF8 as the encoding, and csv as the file format. Click accept and, if everything was processed correctly, you will receive a confirmation notification.</li>
      <li>If you encounter any upload issues, examine the 'energy_data_schema.sql' table and the 'postgres_table.csv' file to ensure all datatypes are aligned. For example, in order for PostgreSQL to correctly populate the GDP column as BIGINT, the GDP column in the 'postgres_table.csv' file must be formatted as a number with zero decimal places.</li>
    </ul>
  <li>Once the PostgreSQL database is configured, the primary ipynb file within the repo contains logic for reading the database via SQLAlchemy. Please note that you will need to update the 'db_uri' variable to align with your own instance of PostgreSQL, where the pattern should be 'postgresql://user_name:password@localhost:port_number/database_name'</li>
</ul>
