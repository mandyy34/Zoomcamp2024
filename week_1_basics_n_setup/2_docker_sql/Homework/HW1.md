Q3
SELECT count(*) FROM public.green_tripdata_201909 where date(lpep_pickup_datetime) = '2019-09-18' and date(lpep_dropoff_datetime) = '2019-09-18'

Q4
SELECT date(lpep_pickup_datetime) FROM public.green_tripdata_201909 where trip_distance = (select max(trip_distance) FROM public.green_tripdata_201909)

Q5
SELECT B."Borough", sum(A.total_amount) FROM public.green_tripdata_201909 A
inner join 
public.taxi_zone_lookup B
on 1 = 1
and A."PULocationID" = B."LocationID"
where date(lpep_pickup_datetime) = '2019-09-18'
group by B."Borough"
having sum(total_amount) > 50000

Q6
SELECT A."tip_amount", C."Zone"  FROM public.green_tripdata_201909 A 
inner join public.taxi_zone_lookup B
on 1 = 1 and A."PULocationID" = B."LocationID"
inner join public.taxi_zone_lookup C
on 1 = 1 and A."DOLocationID" = C."LocationID"
where b."Zone" = 'Astoria'
order by  A."tip_amount" DESC

Q7
google_bigquery_dataset.demo_dataset: Creating... google_storage_bucket.demo-bucket: Creating... google_bigquery_dataset.demo_dataset: Creation complete after 0s [id=projects/precise-rite-412708/datasets/demo_dateset] google_storage_bucket.demo-bucket: Creation complete after 1s [id=precise-rite-412708-terra-bucket]