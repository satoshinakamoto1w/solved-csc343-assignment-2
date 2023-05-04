Download Link: https://assignmentchef.com/product/solved-csc343-assignment-2
<br>
In this assignment, we will work with a database to support a database of <strong>international airports</strong>. Keep in mind that your code for this assignment must work on <em>any </em>database instance (including ones with empty tables) that satisfies the schema.

<h2>Part 1: SQL Statements</h2>

<h3>General requirements</h3>

In this section, you will write SQL statements to perform queries.

To ensure that your query results match the form expected by the autotester (attribute types and order, for instance), we are providing a schema template for the result of each query. These can be found in files q1.sql, q2.sql, …, q5.sql. You must add your solution code for each query to the corresponding file. Make sure that each file is entirely self-contained, and does not depend on any other files; each will be run separately on a fresh database instance, and so (for example) any views you create in q1.sql will not be accessible in q5.sql.

<h3>The queries</h3>

These queries are complex, and we have tried to specify them precisely. Generally speaking, if behaviour is not specified in a particular case, we will not test that case.

Design your queries with the following in mind:

<ul>

 <li>When we say that a passenger <em>took a flight</em>, we mean that the flight was completed, that is, it has gone from departure to arrival. You can assume that if a departure was made, an arrival also occured.</li>

 <li>Each flight has <em>scheduled </em>departure and arrival times, which are the times presented to the passenger upon booking a flight. The <em>actual </em>departure and arrival times arrivals are specified in the Departure and Arrival tables.</li>

 <li>The date that a passenger took the flight is the date of the actual departure (not the scheduled departure time).</li>

 <li>All timestamps are in one time zone (UTC).</li>

</ul>

Write SQL queries for each of the following:

<ol>

 <li>For each passenger, report their passenger ID, full name, and the number of different airlines on which they took a flight.</li>

</ol>

<table width="544">

 <tbody>

  <tr>

   <td width="94"><strong>Attribute</strong></td>

   <td width="450"> </td>

  </tr>

  <tr>

   <td width="94">pass id</td>

   <td width="450">id of a passenger.</td>

  </tr>

  <tr>

   <td width="94">name</td>

   <td width="450">full name of the passenger (for example, Kelly Watts).</td>

  </tr>

  <tr>

   <td width="94">airlines</td>

   <td width="450">the number of different airlines on which they took a flight.</td>

  </tr>

  <tr>

   <td width="94"><strong>Everyone?</strong></td>

   <td width="450">Every passenger should be included, even if they have never taken a flight.</td>

  </tr>

  <tr>

   <td width="94"><strong>Duplicates?</strong></td>

   <td width="450">No passenger can be included more than once.</td>

  </tr>

 </tbody>

</table>

<ol start="2">

 <li><strong>Refunds! </strong>Airlines offer refunds for late departures as follows:</li>

</ol>

For domestic flights (flights within the same country), a 35% refund is given for a departure delay of 4 hours or more, and a 50% refund for 10 hours or more.

For international flights (flights between different countries), a 35% refund is given for a departure delay of 7 hours or more, and a 50% refund for 12 hours or more.

However, if the pilots manage to make up time during the flight and have an arrival delay that is at most <em>half </em>of the departure delay, then no refund is provided, regardless of how many hours the delay was.

For every airline and year that the airline had flights which required refunds, return the <strong>total </strong>refund money given in that particular year in each seat class. This means there should be at most three records per airlineyear combination (you should not include a seat class if no one booked it for any refunded flight). The year of a flight comes from its scheduled departure date.

<table width="692">

 <tbody>

  <tr>

   <td width="94"><strong>Attribute</strong></td>

   <td width="599"> </td>

  </tr>

  <tr>

   <td width="94">airline</td>

   <td width="599">the airline code.</td>

  </tr>

  <tr>

   <td width="94">name</td>

   <td width="599">the airline name.</td>

  </tr>

  <tr>

   <td width="94">year</td>

   <td width="599">a specific year.</td>

  </tr>

  <tr>

   <td width="94">seat class</td>

   <td width="599">one of the three seat classes (economy, business, first).</td>

  </tr>

  <tr>

   <td width="94">refund</td>

   <td width="599">the total money refunded to that seat class that year.</td>

  </tr>

  <tr>

   <td width="94"><strong>Everyone?</strong></td>

   <td width="599">Every airline-year-seat class combination should be included in each year the airline had a flight which required refunds, unless a seat class had no bookings that year for a refunded flight, then you should not include that seat class.</td>

  </tr>

  <tr>

   <td width="94"><strong>Duplicates?</strong></td>

   <td width="599">No duplicates.</td>

  </tr>

 </tbody>

</table>

<ol start="3">

 <li><strong>North and South Connections. </strong>Business passengers that travel between the US and Canada sometimes want to get to their destination on the same day they left, and as early as possible. Because of limited same-day flight options, they may also have to connect through one or two different airports before reaching their destination.</li>

</ol>

Consider the day April 30, 2020 (2020-04-30). For each pair of outbound/inbound <strong>cities </strong>(not airports – a city can have multiple airports) between Canada and the USA (in <strong>both </strong>directions, list the number of possible different routes that a passenger can take on that day to get from the outbound city to the inbound city. You should list the numbers in three different columns: one for the number of direct flight routes (no connections), one for the number of one-connection routes, and one for the number of two-connection routes. In addition, you should include the <strong>earliest possible </strong>arrival time to the inbound city from all of the routes you found.

<em>Note: </em>A minimum connection time of <strong>30 minutes </strong>is required so passengers have a chance to get from one plane to the next.

<table width="625">

 <tbody>

  <tr>

   <td width="94"><strong>Attribute</strong></td>

   <td width="531"> </td>

  </tr>

  <tr>

   <td width="94">outbound</td>

   <td width="531">the outbound city.</td>

  </tr>

  <tr>

   <td width="94">inbound</td>

   <td width="531">the inbound city.</td>

  </tr>

  <tr>

   <td width="94">direct</td>

   <td width="531">the total number of possible direct routes that start and end on April 30, 2020.</td>

  </tr>

  <tr>

   <td width="94">one con</td>

   <td width="531">the total number of possible one-connection routes that start and end on April 30, 2020.</td>

  </tr>

  <tr>

   <td width="94">two con</td>

   <td width="531">the total number of possible two-connection routes that start and end on April 30, 2020.</td>

  </tr>

  <tr>

   <td width="94">earliest</td>

   <td width="531">the earliest possible arrival time (full timestamp) from all of the direct, one-connection, and two-connection routes.</td>

  </tr>

  <tr>

   <td width="94"><strong>Everyone?</strong></td>

   <td width="531">Include all pairs of cities between Canada and the USA in <strong>both </strong>directions (e.g. Toronto to New York <strong>and </strong>New York to Toronto).</td>

  </tr>

  <tr>

   <td width="94"><strong>Duplicates?</strong></td>

   <td width="531">No duplicate outbound/inbound city pairs.</td>

  </tr>

 </tbody>

</table>

<ol start="4">

 <li><strong>Plane capacity histogram. </strong>Create a table that is, essentially, a histogram of the percentages of how full planes have been on the flights that they have made (that is, only the flights that have actually departed). The upper bounds in the ranges below are non-inclusive.</li>

</ol>

<table width="538">

 <tbody>

  <tr>

   <td width="94"><strong>Attribute</strong></td>

   <td width="444"> </td>

  </tr>

  <tr>

   <td width="94">airline</td>

   <td width="444">the airline of the plane.</td>

  </tr>

  <tr>

   <td width="94">tail number</td>

   <td width="444">the tail number of the plane.</td>

  </tr>

  <tr>

   <td width="94">very low</td>

   <td width="444">The number of flights that the plane had between 0% and 20% capacity.</td>

  </tr>

  <tr>

   <td width="94">low</td>

   <td width="444">The number of flights that the plane had between 20% and 40% capacity.</td>

  </tr>

  <tr>

   <td width="94">fair</td>

   <td width="444">The number of flights that the plane had between 40% and 60% capacity.</td>

  </tr>

  <tr>

   <td width="94">normal</td>

   <td width="444">The number of flights that the plane had between 60% and 80% capacity.</td>

  </tr>

  <tr>

   <td width="94">high</td>

   <td width="444">The number of flights that the plane had more than 80% capacity.</td>

  </tr>

  <tr>

   <td width="94"><strong>Everyone?</strong></td>

   <td width="444">Every plane should be included, even if they haven’t flown at all.</td>

  </tr>

  <tr>

   <td width="94"><strong>Duplicates?</strong></td>

   <td width="444">No plane can be included more than once.</td>

  </tr>

 </tbody>

</table>

<ol start="5">

 <li><strong>Flight hopping. </strong>For this query, you are going to learn about and use two interesting features of PostgreSQL: Common Table Expressions and the RECURSIVE</li>

</ol>

A <strong>Common Table Expression </strong>(CTE) is very similar to a VIEW, except instead of saving the view in your schema, you simply use the expression immediately.

You can define a CTE using the WITH clause, and then use it immediately, all within <strong>one </strong>query execution:

WITH air_canada_flights AS                                      — air_canada_flights is the CTE

(SELECT * FROM Flight f

WHERE f.airline = ‘AC’ )

SELECT * from air_canada_flights;

Notice how the semicolon is at the end of the entire query, showing that the CTE declaration (WITH) and the subsequent SELECT statement all happen together, as opposed to separately as in the case of a VIEW.

The RECURSIVE clause allows you to start with a base CTE, and use it to write recursive queries. For example, the query below counts the numbers from 1 to 10:

WITH RECURSIVE numbers AS (

(SELECT 1 AS n)               — the ’base’ query

UNION ALL

(SELECT n + 1 FROM numbers WHERE n &lt; 10) — the recursive query

)

SELECT * FROM numbers;

The base query starts the count by setting the numbers CTE to have only the number 1. Then that CTE is fed into the recursive query, and a table with only the number 2 is produced and assigned to numbers. Then that table is fed into the recursive query and we get 3, and so on until the terminating condition, WHERE n &lt; 10, stops the execution of the recursive queries. We then do a UNION ALL to include all the records from every execution of the recursive query.

You can read more about the RECURSIVE clause here and find examples on how to use it: https://www.postgresqltutorial.com/postgresql-recursive-query/

“Flight hopping” is defined as getting on a plane, landing at a destination, and then within 24 hours getting on another plane from that destination. You can keep doing this, hopping from flight to flight, as long as the time interval between the arrival of one flight and the departure of the next one is less than 24 hours.

Suppose we start at Toronto’s Pearson Airport (YYZ). For a given date and maximum number of flights, list <strong>all </strong>possible airports you can get to on every number of flights up to the maximum by flight hopping, and the number of flights it takes to get to that destination. Keep all airports, even if you could get to them by a different number of flights (up to the max).

Use only scheduled departure and arrival times. We will not enforce a minimum connection time like query 3.

<table width="661">

 <tbody>

  <tr>

   <td width="94"><strong>Attribute</strong></td>

   <td width="567"> </td>

  </tr>

  <tr>

   <td width="94">destination</td>

   <td width="567">an airport code for the final destination of a flight-hopping session.</td>

  </tr>

  <tr>

   <td width="94">num flights</td>

   <td width="567">the number of flights it took to get to that airport through 24-hour flight hopping.</td>

  </tr>

  <tr>

   <td width="94"><strong>Everyone?</strong></td>

   <td width="567">Include all airport destinations you can flight hop to (including the origin airport, YYZ, which would require at least two flights). Include only those from the given start date and <strong>all </strong>number of flights up to the maximum.<strong>The date and maximum number of flights will be provided from the </strong>q5_parameters <strong>relation.</strong></td>

  </tr>

  <tr>

   <td width="94"><strong>Duplicates?</strong></td>

   <td width="567">Duplicates should be included if there are multiple routes that can get you to the same destination in the same number of flights.</td>

  </tr>

 </tbody>

</table>

<h3>SQL Tips</h3>

<ul>

 <li>There are many details of the SQL library functions that we are not covering. It’s just too vast! Expect to use the <a href="https://www.postgresql.org/docs/10/sql.html">postgreSQL documentation</a> to find the things you need. Chapter 9 on functions and operators</li>

</ul>

is particularly useful. Google search is great too, but the best answers tend to come from the postgreSQL documentation.

<ul>

 <li>When subtracting timestamp values, you get a value of type INTERVAL. If you want to compare to a constant time interval, you can do this, for example:</li>

</ul>

WHERE (a – b) &gt; INTERVAL ’0’

Or, you can write an explicit time interval:

WHERE (a – b) &gt; ‘01:30:00’ — greater than 1 hour and 30 minutes.

<ul>

 <li>Please use line breaks so that your queries do not exceed an 80-character line length.</li>

</ul>

<em>Continued on next page…</em>

<h2>Part 2: Embedded SQL</h2>

Imagine an integrated system for an airline that allows passengers and airline workers to perform tasks. This could be something like booking flights for passengers, or seeing an overview of the plane’s current seating arrangements for the check-in counter at the airport. The app could have a graphical user-interface, written in Java, but ultimately it has to connect to the database where the core data is stored. Some of the features will be implemented by Java methods that are merely a wrapper around a SQL query, allowing input to come from gestures the user makes on the app, like button clicks, and output to go to the screen via the graphical user-interface. Other app features will include computation that can’t be done, or can’t be done conveniently, in SQL.

For Part 2 of this assignment, you will not build a user-interface, but will write several methods that the app would need. It would need many more, but we’ll restrict ourselves to just enough to give you practise with JDBC.

<h3>General requirements</h3>

<ul>

 <li>You may not use standard input in the methods that you are completing. Doing so will result in the autotester timing out, causing you to receive a <strong>zero </strong>on that method. (You can use standard input in any testing code that you write outside of these methods, however.)</li>

 <li>You may not change the header of any of the methods we’ve asked you to implement, not even to declare that a method may throw an exception. Each method must have a try-catch clause so that it cannot possibly throw an exception.</li>

 <li>You will be writing a method called connectDb() to connect to the database. When it calls the getConnection() method, it must use the database URL, username, and password that were passed as parameters to connectDb(); these values must not be “hard-coded” in the method. Our autotester will use the connectDb() and disconnectDB() methods to connect to the database with our own credentials.</li>

 <li>You should <strong>not </strong>call connectDb() and disconnectDB() in the other methods we ask you to implement; you can assume that they will be called before and after, respectively, any other method calls.</li>

 <li>All of your code must be written in java. This is the only file you may submit for this part.</li>

 <li>You are welcome to write helper methods to maintain good code quality.</li>

 <li>Carefully read the section on the next page entitled ‘How seats are booked’ to understand the appropriate way to write your methods.</li>

</ul>

<h3>Your task</h3>

Complete the following methods in the starter code in Assignment2.java:

<ol>

 <li>connectDB: Connect to a database with the supplied credentials.</li>

 <li>disconnectDB: Disconnect from the database.</li>

 <li>bookSeat: A method that would be called when a passenger wants to book a seat on a plane.</li>

 <li>upgrade: A method that would be called to see if economy class passengers without a seat can be upgraded to business or first class when economy class is overbooked (more economy bookings than economy seats).</li>

</ol>

You should not call upgrade from bookseat or vice-versa.

<h3>How seats are booked</h3>

Seats are assigned automatically by the system when a passenger books a flight. To keep things consistent, we will constrain this process like so:

<ul>

 <li>In every plane, there are 6 seats per row, designated by the letters A,B,C,D,E, and F. For example, the seat 1E represents the fifth seat in row 1.</li>

 <li>There are three seat classes, first class, which starts at row 1, followed by business class, and then economy.</li>

 <li>When a passenger wants to book a seat in a particular seat class, seats are assigned row by row, from A to F across the row, until the capacity of a seat class is reached. At that point, a new row starts for the next seat class.</li>

</ul>

For example, if there are 8 seats in first class, the seats are booked in this order: 1A, 1B, 1C, 1D, 1E, 1F, 2A, 2B. For the next class, business class, we start on a new row, so the first seat to be booked will be 3A. If there are 15 seats in business class, the last seat in business class will be 5C, and the first seat in economy will be 6A.

<ul>

 <li>Economy class can be overbooked. Up to 10 seats after filling up all economy seats, passengers will not get a seat booked, and instead will have NULL values for the seat number and letter. After 10 NULL seats are booked, no more can be booked.</li>

</ul>

After bookings are done, airline workers can attempt to upgrade NULL seats from economy to a higher seat class, starting with business, followed by first class (with seats assigned in the same order as normal booking). Upgrades are done in order of earliest booking. If there are no seats remaining in the higher classes to upgrade the overbooked seats, then those passengers will unfortunately not be able to take the flight.

You should use these constraints and assumptions when writing your code.

Read the <strong>Javadoc </strong>in the code for more information on what you must do.

<h3>SQL vs. Java</h3>

You will have to decide how much to do in SQL and how much to do in Java. At one extreme, you could use the database for very little other than storage: for each table, you could write a simple query to dump its contents into a data structure in Java and then do all the real work in Java. This is a bad idea. The DBMS was designed to be extremely good at operating on tables! You should use SQL to do as much as it can do for you. In particular, there is no need to use a Java data structure such as an ArrayList, HashMap, or Set, or even a simple array.

We don’t want you to spend a lot of time learning Java for this assignment, so feel free to ask lots of Java-specific questions as they come up.

<h3>Additional JDBC tips</h3>

Some of your SQL queries may be very long strings. You should write them on multiple lines for readability, and to keep your code within an 80-character line length. But you can’t split a Java string over multiple lines. You’ll need to break the string into pieces and use + to concatenate them together. Don’t forget to put a blank at the end of each piece so that when they are concatenated you will have valid SQL. Example:

String sqlText =

“select pass_id ”


“from Passenger r join Booking b on r.pass_id = b.pass_id ” + “where r.fname = ?”;

Note that seat_class is a user-defined type in the ddl file. For a query string, instead of just putting a question mark ?, you should put (?::seat_class), indicating the user-defined type.

Then you can set it in the PreparedStatement, for example: ps.setString(1, “economy”);

Please refer to the JDBC exercise from class for some common mistakes and the error messages they generate.