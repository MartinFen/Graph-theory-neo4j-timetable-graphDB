# GMIT Timetabling Noe4j graph Database

[![Neo4j website](https://upload.wikimedia.org/wikipedia/commons/f/fd/Neo4j-2015-logo.png)](https://neo4j.com/)
###### Martin Fennell, G00291266

## Introduction
This project is for my 3rd year module graph theory which I am using neo4j to represent a prototype timetabling system for a college in graph database form. The project is a small prototype of my current semester with some mildly tidied data that I scraped from the college timetableing website and the gmit website.

#### Aims

The aims of the project are to show I can reperesent a prototype timetabling system using the neo4j software and that I am able to learn how to us it capable to use the software

#### Prerequisits (Getting started)

Below are the tools you need to use this project

1. [Neo4j](https://neo4j.com/download/) - Website where to download neo4j graph database

2. [Regex editor](http://regexr.com/) - Online Regex editor (This is optional as info is supplied)

3. [Notepad++](https://notepad-plus-plus.org/) - Text editor that can use regex and create/use csv files

## Database

#### Nodes

Nodes are a way of storing and entity in neo4j so a person is an entity.

The nodes of the database are as follows,

| Node(Node label) | Description |
| ------ | ------ |
| Campus | node(s) to represent the campuses of the college |
| Course | node(s) to represent the course(s) of the college |
| Department | node(s) to represent the department(s) of the college |
| Lecturer | node(s) to represent the lecturer(s) of the college |
| Rooms | node(s) to represent the room(s) in a campus |
| Time slots | node(s) to represent the times(s) that classes were in session |
| Group | node(s) to represent the group(s) in a course |
| Module | node(s) to represent the modules(s) of a course |
| Student | node(s) to represent the students(s) of the college |

To create the nodes I used a cypher command called [Load CSV]() which allowed me to store the data I scraped in csv files
then load the data in and create a group of nodes. An example command I used to create nodes is as follows,
```
LOAD CSV WITH HEADERS FROM "file:///C:/LecturersTidy.csv" AS csvLine
CREATE (n:Lecturer {title: csvLine.Title, surname: csvLine.Surname, firstname: csvLine.FName, campus: csvLine.Campus, extension: csvLine.Extension, contact: csvLine.Contact, email: csvLine.Email})
```
#### Properties

Properties are inside nodes and are used to contain data.

as seen below,

| Property || Description |
| ------ || ------ |
| firstname || property that contains data such as a lecturers first name|

The properties of the lecture nodes were created along with the nodes using the th [load CSV]() command as follows,
```
LOAD CSV WITH HEADERS FROM "file:///C:/LecturersTidy.csv" AS csvLine
CREATE (n:Lecturer {title: csvLine.Title, surname: csvLine.Surname, firstname: csvLine.FName, campus: csvLine.Campus, extension: csvLine.Extension, contact: csvLine.Contact, email: csvLine.Email})
```

#### Relationships

Relationships are the way that nodes can be connected together

#### Labels

#### Functions

#### Neo4j

- talk about neo4j

#### Cypher

- talk about cypher(What the hell is it and what does it do)

## Implementation 

#### Data extraction

#### Data Implementation

#### Cypher Queries

> There are queries I used to search the nodes of the database
> Match n Return n;

## Design Decisions (Not implementated but useful)

Below here are design ideas that I chose not to go ahead with as they did not suit the project design in this case but are useful for future projects.

#### Graphaware framework / Timetree library

The [graphaware](https://graphaware.com/) framework is a useful one that works with neo4j and spring(Java) which also uses a REST api. It can be used with neo4j by itself to quickly create a tree of nodes and relationships to reperesent date & time as neo4j doesnt have a very good built in way of designing that and this also saves you time in having to design a calander for a long date range.

#### How to use

To enable the framework you need to [download the jar](https://graphaware.com/products/) file put it in the plugin folder of the neo4j install directory `C:\Program Files\Neo4j CE 3.1.2\plugins`.

You then need to edit the neo4j.conf file by adding the following line to the file,
`dbms.unmanaged_extension_classes=com.graphaware.server=/graphaware`

To use the timetree library you need to [download the jar](https://graphaware.com/products/), do the same as before and put the jar in the plugin folder `C:\Program Files\Neo4j CE 3.1.2\plugins`.

Then restart the neo4j server and log into your db.

The next step is to run a query try the following and see that it creates a tree with nodes, relationships and properties for `yyyy-mm-dd`.

```sh
$ CALL ga.timetree.range({start: 1491811200000, end: 1492189200000, create: true})
```

[![Result](https://github.com/MartinFen/Graph-theory-neo4j-timetable-graphDB/blob/master/Timetree_example2.jpg)]

Note the numbers in the query, Neo4j measures the time in milliseconds between the dates of `2017-04-10 to 2017-04-14` however the first number is actualy the time its been since the [Unix Epoch](https://en.wikipedia.org/wiki/Unix_time).

#### Reasons for not using this approach

I didnt use these plugins because it would'nt work in this project, I chose to not use tools and go with a simpler design because I was having issues with getting the framework to build the nodes that had `weekday names` that matched the date nodes, I also had an issue to change the `resolution : default is day` to `hours`. I felt it was better then to go with a simple prototype design for the day & time representation in the database.

## References

### Neo4j,

- [Neo4j](https://neo4j.com)

- [Neo4j docs](https://neo4j.com/developer/get-started/)

### Data extraction

- [GMIT Timetabling website](https://timetable.gmit.ie/)

- [GMIT website](https://www.gmit.ie/)

### Regex

- [Regex editor](http://regexr.com/)

- [Cheat sheet](https://www.cheatography.com/davechild/cheat-sheets/regular-expressions/)

#### Most helpful regex

- [For questions I had](https://stackoverflow.com/)

- [Remove html tags](https://www.rhyous.com/2012/12/11/removing-all-xml-or-html-tags-using-notepad/)

- [Find a number between brackets](http://stackoverflow.com/questions/13807207/regex-find-a-number-between-parentheses)

- [Remove numbers inside backets](http://stackoverflow.com/questions/38962471/only-remove-numbers-inside-parentheses-brackets)

### Github (Markdown)

- [Live markdwn editor](http://dillinger.io/)

### Cypher

- [Learning cypher 1](https://neo4j.com/developer/cypher-query-language/)

- [Learning cypher 2](http://neo4j.com/docs/developer-manual/current/cypher/)

- [Loading csv files](http://neo4j.com/docs/developer-manual/current/get-started/cypher/importing-csv-files-with-cypher/)

### Un-Used

- [Graphaware Github](https://github.com/graphaware/neo4j-framework)

- [Timetree Github](https://github.com/graphaware/neo4j-timetree)


