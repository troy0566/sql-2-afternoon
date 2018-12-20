Practice Joins
1)
select * from Invoice 
where invoiceId in (select InvoiceId from InvoiceLine 
                    where UnitPrice > .99)

2)
SELECT Inv.InvoiceDate, Cust.FirstName, Cust.LastName, Inv.Total 
FROM Invoice Inv, Customer Cust
Where Inv.CustomerId = Cust.CustomerId

3)
SELECT Cust.FirstName, Cust.LastName, Emp.FirstName, Emp.LastName 
FROM  Customer cust, Employee Emp
Where Cust.SupportRepId = Emp.EmployeeId

4)
SELECT Album.Title, Artist.Name 
FROM Album, Artist
WHERE Album.ArtistId = Artist.ArtistId

5)
SELECT pt.TrackId
FROM PlaylistTrack pt
JOIN Playlist p ON p.PlaylistId = pt.PlaylistId
WHERE p.Name = 'Music';

6)
SELECT Name 
FROM Track 
WHERE TrackID IN (SELECT TrackId 
                  FROM PlaylistTrack 
                  WHERE PlaylistId IN (SELECT PlaylistId 
                                       FROM Playlist 
                                       WHERE PlaylistId = 5))
7)
SELECT t.name, p.Name
FROM Track t
JOIN PlaylistTrack pt ON t.TrackId = pt.TrackId
JOIN Playlist p ON pt.PlaylistId = p.PlaylistId;

8)
SELECT t.Name, a.title
FROM Track t
JOIN Album a ON t.AlbumId = a.AlbumId
JOIN Genre g ON g.GenreId = t.GenreId
WHERE g.Name = "Alternative";

Practice nested queries

1)
select * from Invoice 
where invoiceId in (select InvoiceId from InvoiceLine 
                    where UnitPrice > .99)
2) 
SELECT * 
FROM PlaylistTrack PT
WHERE PT.PlaylistId in (SELECT PlayListId 
                        FROM Playlist 
                        where Name = 'Music');
3)
SELECT Name 
FROM Track 
WHERE TrackID IN (SELECT TrackId 
                  FROM PlaylistTrack 
                  WHERE PlaylistId IN (SELECT PlaylistId 
                                       FROM Playlist 
                                       WHERE PlaylistId = 5))
4)
SELECT Track.Name 
FROM Track 
WHERE Track.GenreId in (SELECT Genre.GenreId 
                        FROM Genre 
                        WHERE NAME='Comedy')
5)
SELECT Name 
FROM Track 
WHERE AlbumId in (SELECT AlbumId 
                  FROM Album 
         		  WHERE Title ='Fireball')
6)
SELECT Name 
FROM Track 
Where AlbumId IN (SELECT AlbumId 
                  FROM Album 
                  WHERE ArtistId IN (SELECT ArtistId 
                                      FROM Artist 
                                      WHERE NAME = 'Queen'))

Practice updating Rows

1)
UPDATE Customer SET Fax = Null
WHERE Fax IS NOT NULL;
2)
UPDATE Customer SET Company = "Self"
Where Company IS Null
3)
UPDATE Customer SET LastName = "Thompson"
WHERE FirstName = "Julia" and LastName = "Barnett";
4)
UPDATE Customer SET SupportRepId = 4
WHERE Email = "luisrojas@yahoo.cl";
5)
UPDATE TRACK SET Composer = "The darkness around us" 
WHERE Composer IS NULL 
AND Track.GenreId in (SELECT Genre.GenreId 
                           FROM Genre 
                           WHERE NAME='Metal')

Group By

1)
SELECT Genre.Name, Count(TrackId)
FROM Track 
Join Genre ON Track.GenreId = Genre.GenreId
Group by Genre.Name;
2)
SELECT Genre.Name, Count(TrackId)
FROM Track 
Join Genre ON Track.GenreId = Genre.GenreId
WHERE Genre.Name = "Pop" or Genre.Name = "Rock"
Group By Genre.Name
3)
SELECT Artist.Name, Count(AlbumId)
FROM Album
Join Artist on Album.ArtistId = Artist.ArtistId
Group By Album.ArtistId

Use Distinct

1)
SELECT DISTINCT Composer
FROM TRACK;
2)
SELECT DISTINCT BillingPostalCode
FROM Invoice;
3)
SELECT DISTINCT Company
FROM Customer;

Delete Rows
1)
Done
2)
DELETE FROM practice_delete 
WHERE Type = "bronze"; 
3)
DELETE FROM practice_delete 
WHERE Type = "silver";
4)
DELETE FROM practice_delete 
WHERE Value = 150;