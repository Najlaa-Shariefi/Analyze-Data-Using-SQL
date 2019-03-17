

/*Query 1 - the query used for first insight */
SELECT m.Name AS MediaType ,
       SUM(i.Quantity) AS QuantityPurchased
FROM MediaType m
JOIN Track t
ON m.MediaTypeId = t.MediaTypeId
JOIN InvoiceLine i
ON t.TrackId = i.TrackId
GROUP BY 1
ORDER BY 2 DESC;


 /*Query 2 - the query used for second insight */
 SELECT ar.Name As ArtistName ,
        COUNT( t.TrackId ) AS NumberOfTracks
 FROM Artist ar
 JOIN Album al
 ON ar.ArtistId = al.ArtistId
 JOIN Track t
 ON t.AlbumId = al.AlbumId
 GROUP BY 1
 ORDER BY  2 DESC
 LIMIT 5;


/*Query 3 - the query used for third insight */
SELECT g.Name AS GenreName  ,
       COUNT (t.TrackId) AS NumberOfTracks
FROM  Track t
JOIN Genre g
ON g.GenreId = t.GenreId
GROUP BY 1
ORDER BY 2 DESC
LIMIT 5;


/*Query 4 - the query used for fourth insight */
SELECT ar.Name As ArtistName ,
       ROUND(SUM(il.Quantity*il.unitprice),0) AS TotalRevenue
FROM Artist ar
JOIN Album al
ON ar.ArtistId = al.ArtistId
JOIN Track t
ON al.AlbumId = t.AlbumId
JOIN InvoiceLine il
ON il.TrackId = t.TrackId
Group BY 1
Order BY 2 DESC
LIMIT 5;
