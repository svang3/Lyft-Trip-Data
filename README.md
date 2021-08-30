# Codecademy -- Lyft-Trip-Data

/* examine the three tables */
select * from trips;

select * from riders;

select * from cars;

/* The primary key of trips, riders, and cars is id */

/* cross join riders and cars */
select riders.first,
   riders.last, cars.model
from riders, cars;
/* result is not useful since it combines each user with every car model. */

/* search for columns to join between trips and riders and combine the two tables using left join */
select * from trips
left join riders
  on trips.rider_id = riders.id;

/* search for columns to join on and combine the trips and cars table using inner join */
select * from trips
join cars
  on trips.car_id = cars.id;

/* stack riders table on top of the new table name riders2 */
select * from riders
union
select * from riders2;

/* average cost for a trip */
select round(avg(cost), 2) from trips;

/* search all riders who have used Lyft less than 500 times */
select * from riders
where total_trips < 500;

/* calculate the number of cars that are active */
select count(*) from cars
where status = 'active';

/* finds two cars that have the highest trips completed */
select * from cars
order by trips_completed desc
limit 2;
