-- 1 Tables
create table account(
id number constraint pk_id primary key,
name varchar2(20) not null,
pass number,
birth date,
email varchar2(20),
plan number
);
/
create table genre(
id number constraint pk_ge primary key,
name varchar2(20)
);
/
create table artist(
id number constraint pk_ar primary key,
name varchar2(20)
);
/
create table album(
id number constraint pk_al primary key,
ar_id number not null constraint fk_al_ar references artist(id),
name varchar2(20) not null,
rel date
);
/
create table song(
id number constraint pk_so primary key,
name varchar2(20) not null,
album_id number not null constraint fk_so_al references album(id),
genre_id number not null constraint fk_so_ge references genre(id)
);
/
create table podcast(
id number constraint pk_po primary key,
name varchar2(20) not null,
ar_id number not null constraint fk_po_ar references artist(id),
des varchar2(300)
);
/
create table episode(
id number constraint pk_ep primary key,
name varchar2(20) not null,
po_id number not null constraint fk_ep_po references podcast(id),
des varchar2(300),
dur number
);

create table playlist(
id number constraint pk_pl primary key,
name varchar2(20) not null,
des varchar2(300),
ac_id number not null constraint fk_pl_ac references account(id)
);
/
create table nub(
id number constraint pk_nu primary key,
pl_id number not null constraint fk_nu_pl references playlist(id),
so_id number not null constraint fk_nu_so references song(id),
da date
);
/
create table history(
id number constraint pk_hi primary key,
des varchar2(100),
us varchar2(100),
da date
);
/
-- 4 Sequences
/
create sequence s_account start with 1 increment by 1 nomaxvalue;
create sequence s_genre start with 1 increment by 1 nomaxvalue;
create sequence s_artist start with 1 increment by 1 nomaxvalue;
create sequence s_album start with 1 increment by 1 nomaxvalue;
create sequence s_song start with 1 increment by 1 nomaxvalue;
create sequence s_podcast start with 1 increment by 1 nomaxvalue;
create sequence s_episode start with 1 increment by 1 nomaxvalue;
create sequence s_playlist start with 1 increment by 1 nomaxvalue;
create sequence s_nub start with 1 increment by 1 nomaxvalue;
create sequence s_history start with 1 increment by 1 nomaxvalue;
/
-- 5 Insert Triggers
/
create or replace trigger t_i_account
after insert on account
begin
    insert into history values (s_history.nextVal, 'insert -> account', user, sysdate);
end;
/
create or replace trigger t_i_genre
after insert on genre
begin
    insert into history values (s_history.nextVal, 'insert -> genre', user, sysdate);
end;
/
create or replace trigger t_i_artist
after insert on artist
begin
    insert into history values (s_history.nextVal, 'insert -> artist', user, sysdate);
end;
/
create or replace trigger t_i_album
after insert on album
begin
    insert into history values (s_history.nextVal, 'insert -> album', user, sysdate);
end;
/
create or replace trigger t_i_song
after insert on song
begin
    insert into history values (s_history.nextVal, 'insert -> song', user, sysdate);
end;
/
create or replace trigger t_i_podcast
after insert on podcast
begin
    insert into history values (s_history.nextVal, 'insert -> podcast', user, sysdate);
end;
/
create or replace trigger t_i_episode
after insert on episode
begin
    insert into history values (s_history.nextVal, 'insert -> episode', user, sysdate);
end;
/
create or replace trigger t_i_playlist
after insert on playlist
begin
    insert into history values (s_history.nextVal, 'insert -> playlist', user, sysdate);
end;
/
create or replace trigger t_i_nub
after insert on nub
begin
    insert into history values (s_history.nextVal, 'insert -> nub', user, sysdate);
end;
/
-- 6 Delete Triggers
create or replace trigger t_d_account
after delete on account
begin
    insert into history values (s_history.nextVal, 'delete -> account', user, sysdate);
end;
/
create or replace trigger t_d_genre
after delete on genre
begin
    insert into history values (s_history.nextVal, 'delete -> genre', user, sysdate);
end;
/
create or replace trigger t_d_artist
after delete on artist
begin
    insert into history values (s_history.nextVal, 'delete -> artist', user, sysdate);
end;
/
create or replace trigger t_d_album
after delete on album
begin
    insert into history values (s_history.nextVal, 'delete -> album', user, sysdate);
end;
/
create or replace trigger t_d_song
after delete on song
begin
    insert into history values (s_history.nextVal, 'delete -> song', user, sysdate);
end;
/
create or replace trigger t_d_podcast
after delete on podcast
begin
    insert into history values (s_history.nextVal, 'delete -> podcast', user, sysdate);
end;
/
create or replace trigger t_d_episode
after delete on episode
begin
    insert into history values (s_history.nextVal, 'delete -> episode', user, sysdate);
end;
/
create or replace trigger t_d_playlist
after delete on playlist
begin
    insert into history values (s_history.nextVal, 'delete -> playlist', user, sysdate);
end;
/
create or replace trigger t_d_nub
after delete on nub
begin
    insert into history values (s_history.nextVal, 'delete -> nub', user, sysdate);
end;
/
-- Procedures
/
create or replace procedure p_i_account(na varchar2, pass number, birth varchar2, email varchar2, plan number)
as begin
    insert into account values(s_account.nextVal, na, pass, to_date(birth,'YYYY-MM-DD'), email, plan);
end;
/
create or replace procedure p_i_genre(na varchar2)
as begin
    insert into genre values(s_genre.nextVal, na);
end;
/
create or replace procedure p_i_artist(name varchar2)
as begin
    insert into artist values(s_artist.nextVal, name);
end;
/
create or replace procedure p_i_album(ar number, na varchar2, release varchar2)
as begin
    insert into album values(s_album.nextVal, ar, na, to_date(release,'YYYY-MM-DD'));
end;
/
create or replace procedure p_i_song(na varchar2, alb number, gen number)
as begin
    insert into song values(s_song.nextVal, na, alb, gen);
end;
/
create or replace procedure p_i_podcast(na varchar2, ar number, des varchar2)
as begin
    insert into podcast values(s_podcast.nextVal, na, ar, des);
end;
/
create or replace procedure p_i_episode(na varchar2, pod number, des varchar2, du number)
as begin 
    insert into episode values(s_episode.nextVal, na, pod, des, du);
end;
/
create or replace procedure p_i_playlist(na varchar2, des varchar2, acc number)
as begin
    insert into playlist values(s_playlist.nextVal, na, des, acc);
end;
/
create or replace procedure p_i_nub(pl number, so number)
as begin
    insert into nub values(s_nub.nextVal, pl, so, sysdate);
end;
/
--Executes
/
execute p_i_account('petrucci', 1234, '1967-07-12', 'jp@dt.com', 2);
execute p_i_account('portnoy', 1234, '1969-03-23', 'mp@dt.com', 1);
execute p_i_account('labrie', 1234, '1963-05-05', 'jlb@dt.com', 0);
execute p_i_account('myung', 1234, '1967-01-24', 'jm@dt.com', 1);
execute p_i_account('rudess', 1234, '1956-11-04', 'jr@dt.com', 2);
execute p_i_genre('rock');
execute p_i_genre('pop');
execute p_i_genre('metal');
execute p_i_genre('death metal');
execute p_i_genre('prog metal');
execute p_i_artist('Van Halen');
execute p_i_artist('Bon Jovi');
execute p_i_artist('Haken');
execute p_i_artist('Necrophagist');
execute p_i_artist('Opeth');
execute p_i_album(1,'Balance','1986-03-24');
execute p_i_album(1,'5150','1986-03-24');
execute p_i_album(3,'Affinity','2016-04-29');
execute p_i_album(4,'Epitaph','2004-08-03');
execute p_i_album(5,'Ghost Reveries','2005-08-29');
execute p_i_song('Cant stop loving you',1,1);
execute p_i_song('Bound by gravity',3,5);
execute p_i_song('Harlequin forest',5,4);
execute p_i_song('Stabwound',4,4);
execute p_i_song('The architect',3,5);
execute p_i_playlist('playlist de myung','de todo',4);
execute p_i_playlist('megaplaylist','haken',2);
execute p_i_playlist('superplaylist','opeth',2);
execute p_i_podcast('Bon podcast',2,'podcast de bon jovi');
execute p_i_podcast('Bon podcast 2',2,'electric boogaloo');
execute p_i_episode('Capitulo 1',1,'descripcion',30);
execute p_i_episode('Capitulo 2',1,'segunda parte',34);
execute p_i_episode('Na q ver',2,'charla',45);
execute p_i_episode('En vivo',2,NULL,40);
execute p_i_episode('Acercandose',2,NULL,20);
execute p_i_nub(1,1);
execute p_i_nub(1,2);
execute p_i_nub(1,3);
execute p_i_nub(1,4);
execute p_i_nub(1,5);
execute p_i_nub(2,2);
execute p_i_nub(2,5);
execute p_i_nub(1,3);
execute p_i_nub(3,3);
/
select * from playlist;
select * from song;
select * from nub;
-- 8 Views
create or replace view accounts as
select id as "ID", name as "Name", '****' as "Password", birth as "Birthday", email as "e-mail", plan as "Plan"
from account
order by id asc;
/
create or replace view albums as
select id as "ID", ar_id as "Artist", name as "Album Name", rel as "Release Date"
from album
order by id asc;
/
create or replace view artists as
select id as "ID", name as "Artist Name"
from artist
order by id asc;
/
create or replace view episodes as
select id as "ID", name as "Episode Name", po_id as "Podcast", des as "Description", dur as "Duration [s]"
from episode
order by id asc;
/
create or replace view genres as
select id as "ID", name as "Genre Name"
from genre
order by id asc;
/
create or replace view playlists as
select id as "ID", name as "Playlist Name", des as "Description", ac_id as "Account"
from playlist
order by id asc;
/
create or replace view podcasts as
select id as "ID", name as "Podcast Name", ar_id as "Artist", des as "Description"
from podcast
order by id asc;
/
create or replace view songs as
select id as "ID", name as "Song Name", album_id as "Album", genre_id as "Genre"
from song
order by id asc;
/
create or replace view nubs as
select id as "ID", pl_id as "Playlist ID", so_id as "Song ID", da as "Date added"
from nub
order by id asc;
/
--------------------------------------------------------------------------------
-- 9
-- 2 tables, 3 values, 1 sum
select podcast.name as "Podcast", sum(dur) as "Suma duraciones",
max(dur) as "Episodio mas largo", min(dur) as "Episodio mas corto"
from podcast inner join episode
on podcast.id = episode.po_id
group by podcast.name;
/
-- 10
-- 3 vews, like -> compound name songs
select "Song Name", "Album Name", "Genre Name" from genres
inner join songs on "Genre" = genres.id
inner join albums on "Album" = albums.id
where "Song Name" like '% %'
order by genres.id asc;
/
-- 11
-- 5 data, 2 tables, formatted date
select playlist.name, playlist.des, playlist.ac_id, nub.so_id, to_char(nub.da,'DAY MONTH YYYY HH24:MI:SS')
from playlist inner join nub
on nub.pl_id = playlist.id;
/
-- 12
-- 5 data, 2 views minimum, formatted date
select to_char("Date added",'DD-MM-YYYY HH24:MI:SS') as "Ins Date", "Song Name", "Playlist Name", "Description", "Account" 
from playlists
inner join nubs on playlists.id = "Playlist ID"
inner join songs on songs.id= "Song ID";
/
-- 13
-- 3 data, initcap, length, hh >=
select to_char(da,'HH24:MI:SS') as "Date >= 11:45", initcap(name) as "Initcap" , length(name) as "Length" from 
nub inner join song on song.id = nub.so_id 
where to_date(to_char(da,'HH24:MI:SS'), 'HH24:MI:SS') >= to_date('11:45:00','HH24:MI:SS');
/
-- 14
-- 3 data,  INSTR & SUBSTR, subquery as condition.
select substr(name,8,5) as "substr", album_id as "Album ID", genre_id as "Genre ID" from song
where album_id = (select max(INSTR(name, 'e')) from song);
/
-- 15
-- 3 data, lpad rpad on same field, condition
select s.id as "Song ID", s.name as "Song Name", rpad(lpad(g.name,15,'*'),20,'*') as "Genre"
from genre g inner join song s
on g.id=s.genre_id
where s.id > 2;
/
--16
-- 3 data, nvl & replace, replace NULL & "A"
select replace(episode.name,'A','X') as "Episode Name (Replace)", 
NVL(episode.des,'--No Description--') as "Description (NVL)", podcast.name as "Podcast Name" 
from episode inner join podcast on episode.po_id = podcast.id;
/
-- 17
-- Procedure to modify table through ID, which will be used as a parameter along with the new data to update
create or replace procedure p_u_account(row number, na varchar2, pa number, bi varchar2, em varchar2, pl number)
as begin   
    update account set name=na, pass=pa, birth=to_date(bi,'YYYY-MM-DD'), email=em, plan=pl where id=row;
end;
/
-- 18
-- Fuction without parameters, which gives ammount, sum or average (1 of the 3)
create or replace function count_genre
return number
is
    res number;
begin
    select count(*) into res from genre;
    return res;
Exception when No_Data_Found then return 0;
end;
/
-- 19
-- Function with 1 parameter, which filters information and obtains ammount, sum or average (1 of the 3)
create or replace function sum_dur_episode(po number)
return number
is
    res number;
begin
    select sum(dur) into res from episode where po_id = po;
    return res;
Exception when No_Data_Found then return 0;
end;
/
-- 20
-- Delete all previously created objects
drop function sum_dur_episode;
drop function count_genre;
drop procedure p_u_account;
drop procedure p_i_account;
drop procedure p_i_genre;
drop procedure p_i_artist;
drop procedure p_i_album;
drop procedure p_i_song;
drop procedure p_i_playlist;
drop procedure p_i_podcast;
drop procedure p_i_episode;
drop procedure p_i_nub;
drop view accounts;
drop view genres;
drop view artists;
drop view songs;
drop view playlists;
drop view podcasts;
drop view episodes;
drop view nubs;
drop view albums;
drop trigger t_d_account;
drop trigger t_d_genre;
drop trigger t_d_artist;
drop trigger t_d_song;
drop trigger t_d_playlist;
drop trigger t_d_podcast;
drop trigger t_d_episode;
drop trigger t_d_nub;
drop trigger t_i_account;
drop trigger t_i_genre;
drop trigger t_i_artist;
drop trigger t_i_song;
drop trigger t_i_playlist;
drop trigger t_i_podcast;
drop trigger t_i_episode;
drop trigger t_i_nub;
drop sequence s_account;
drop sequence s_genre;
drop sequence s_artist;
drop sequence s_album;
drop sequence s_song;
drop sequence s_podcast;
drop sequence s_episode;
drop sequence s_playlist;
drop sequence s_nub;
drop sequence s_history;
drop table history;
drop table nub;
drop table playlist;
drop table episode;
drop table podcast;
drop table song;
drop table album;
drop table artist;
drop table genre;
drop table account;
