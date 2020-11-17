

### Overview
- Upsert
- Liquibase and Changelogs
- ByteArrays
- Docker
- Work never stops

This week I was working with extracting data from an API and building a pipeline to capture it in the database, so everything I learned this week was oriented this way.

***
### Upsert
This was very helpful while capturing the data form the API and inserting it in the database, mainly because the API repeats data a lot of times. The upsert basically helps us to make some kind of validation, we try to insert and if we can't because some conflict we can proceed to another action, like updating.
For example:

```java
                String SQL = "INSERT INTO team(id,name,city,logo,logo_content_type,sport_type_id)" +
                    "VALUES(?, ?, ?, ?, ?, ?)" +
                    "ON CONFLICT (id)"+
                    "DO UPDATE SET local_score ="+ localScore + "," + "visitor_score =" visitorScore;
```
We can do an upsert in postgresql using java like the previous snippet. So we can achieve that everytime that we see a repetead id, it will change the score of the match to the final score.

***
### Liquibase and Changelogs
I had never worked with anything similar to Liquibase, but it was an interesting experience.
Liquibase is basically a tool that helps us have all of our migrations registered in changelogs to keep a track of all changes. Basically is a git for databases. I had a lot of problems while working on this, because once the changelogs doesn't add up it will cause a conflict.
For example, you can create a table like this using an xml format:

```xml
<changeSet id="20201104182139-1" author="jhipster">
        <createTable tableName="sports_event">
            <column name="id" type="bigint">
                <constraints primaryKey="true" nullable="false"/>
            </column>
            <column name="title" type="varchar(50)">
                <constraints nullable="false" />
            </column>
            <column name="description" type="varchar(300)">
                <constraints nullable="true" />
            </column>
        </createTable>
        <dropDefaultValue tableName="sports_event" columnName="date" columnDataType="datetime"/>
    </changeSet>
```

The problem comes when you are unexperienced and you just want to add a column so you decided to directly modify the file. Spoiler: it doesn't work.
So the solution can be creating another file into your changelog directory and add something like this:

```xml
    <changeSet id="20201116210620-1" author="jhipster">
        <addColumn catalogName="tables"
                   schemaName= "public"
                   tableName="sports_event" >
            <column name="local_score"
                    type="integer"/>
        </addColumn>
        <addColumn catalogName="tables"
                   schemaName= "public"
                   tableName="sports_event" >
            <column name="visitor_score"
                    type="integer"/>
        </addColumn>
        <addColumn catalogName="tables"
                   schemaName= "public"
                   tableName="sports_event" >
            <column name="status"
                    type="varchar"/>
        </addColumn>
    </changeSet>
```

***
### Byte Arrays
When you want to insert an image to a database like postgresql, you do it like a bytea (byte array).
This is how I did it in java:
```java
        public static byte[] recoverImageFromUrl(String urlText) throws Exception {
            URL url = new URL(urlText);
            ByteArrayOutputStream output = new ByteArrayOutputStream();

            try (InputStream inputStream = url.openStream()) {
                int n = 0;
                byte [] buffer = new byte[ 1024 ];
                while (-1 != (n = inputStream.read(buffer))) {
                    output.write(buffer, 0, n);
                }
            }

            return output.toByteArray();
        }
```

And then I added this to implement the method:
```java
statement.setBytes(4, recoverImageFromUrl(logo));
```

Basically this methods takes a url and creates an object of type `ByteArrayOutputStream` that allow us to insert the image .png to the database. We iterate trough the bytes until we finish with the image and we can return it.

***
### Docker
I had never used docker before, but this week I had the chance to work with it. We just created a container with postgresql to set the database. I found out that you can run this very easily using IntelliJ, all the purists are going to help me but I only used the GUI from IntelliJ to implement this.
You just basically edit some configurations add some user name, password, url, click some buttons and there you go. IntelliJ does the magic.

***
### Work never stops
This week I learned that you need to learn when to stop working. No matter how much you work, you will never end. You need to set a timebox for the things you're going to work on, give it your best shot and when the time is up you stop. IMO this is the most healthy approach.
I'm talking about this because this week I had the chance to experience an endless workload, so I think in this cases is better to communicate why you can't complete it and give it your best for a determined period of time. I want to clarify that I'm not saying that you shouldn't work hard, I'm all about hard work, but staying healthy mentally and physically should be a priority.
