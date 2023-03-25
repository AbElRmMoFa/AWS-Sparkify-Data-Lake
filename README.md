# AWS-Sparkify-Data-Lake
<h1>Project Overview</h1>
<p>Sparkify is a music streaming startup that has grown their user base and song database even more and want to move their data warehouse to a data lake. Their data resides in S3, in a directory of JSON logs on user activity on the app, as well as a directory with JSON metadata on the songs in their app.</p>

<h2>Project Goals</h2>
<ul>
  <li>Build an ETL pipeline that extracts their data from S3, processes them using Spark, and loads the data back into S3 as a set of dimensional tables.</li>
  <li>Deploy this Spark process on a cluster using AWS.</li>
  <li>Provide data analysts with an easy-to-use way to query the data using Spark SQL.</li>
</ul>

<h2>Schema Design</h2>
<p>The schema design is a star schema optimized for queries on song play analysis. It consists of the following tables:</p>
<ul>
  <h3>Fact Table</h3>
<ul>
    <li><code>songplays</code> - records in log data associated with song plays i.e. records with page <code>'NextSong'</code></li>
    <li><code>songplays</code> table has the following columns: <code>songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent</code></li>
</ul>
<h3>Dimension Tables</h3>
<ul>
    <li><code>users</code> - users in the app<br>
        <code>users</code> table has the following columns: <code>user_id, first_name, last_name, gender, level</code></li>
    <li><code>songs</code> - songs in music database<br>
        <code>songs</code> table has the following columns: <code>song_id, title, artist_id, year, duration</code></li>
    <li><code>artists</code> - artists in music database<br>
        <code>artists</code> table has the following columns: <code>artist_id, name, location, latitude, longitude</code></li>
    <li><code>time</code> - timestamps of records in <code>songplays</code> broken down into specific units<br>
        <code>time</code> table has the following columns: <code>start_time, hour, day, week, month, year, weekday</code></li>
</ul>

<h2>ETL Process</h2>
<p>The ETL process consists of the following steps:</p>
<ol>
  <li>Load data from S3</li>
  <li>Process data using Spark to extract the necessary columns for each table and transform them into the right format</li>
  <li>Load the data back into S3 as parquet files</li>
</ol>

<h2>File Descriptions</h2>
<ul>
  <li><strong>etl.py:</strong> contains the ETL pipeline that extracts the data from S3, processes it, and loads it back into S3.</li>
  <li><strong>dl.cfg:</strong> contains AWS credentials.</li>
</ul>

<h2>How to Run</h2>
<ol>
  <li>Fill in the AWS credentials in dl.cfg.</li>
  <li>Run etl.py.</li>
</ol>
