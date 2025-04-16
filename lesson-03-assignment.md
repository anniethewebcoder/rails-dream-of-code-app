# LESSON 03 ASSIGNMENT

by Annie Kwon

1. What tables do you need to add? Decide on table names and their associations to each other and any existing tables/models.

- `topics`, `lesson_topic`
- `lesson_topic` table would be associated with `topics` and `lessons` tables. That way, `topics` and `lessons` would have many-to-many relationship.

2. What columns are necessary for the associations you decided on?

- `lesson_topic` has `lesson_id` and `topic_id` columns.
- `topics` table has `title` and `description` columns.

3. What other columns (if any) need to be included on the tables? What other data needs to be stored?

- I don't see any (for now)

4. Write out each table's name and column names with data types.

| table: topic                 |
| ---------------------------- |
| **id**: integer, primary key |
| **title**: string            |
| **description**: text        |

| table: lesson_topic                 |
| ----------------------------------- |
| **id**: integer, primary key        |
| **lesson_id**: integer, foreign key |
| **topic_id**: intger, foreign key   |

5. Determine the generator command you'll need to create the migration file and run the command to generate the empty migration file. **Start with just the topics migration.** (Hint: your filename should be `create_topics`)

```ruby
    bin/rails generate migration create_topics
```

6. Inside the `create_table` block in the migration file, add the appropriate columns and datatypes.

```ruby
    bin/rails generate migration CreateTopics title:string description:text
```

7. Run the migration with `bin/rails db:migrate` (in a terminal window, not a rails console). Watch the output and make sure it is successful before moving on. (You can check the database to see if your table exists.)

```ruby
    Topic.create!(

    )
```

8. Add the `Topic` model before moving on.

- `models/topic.rb`

```ruby
    class Topic < ApplicationRecord
    end
```

9. Now determine the generator command you'll need to create the migration file for the join table. Don't forget that it should begin with `create_` and be followed by the table name.

```ruby
    bin/rails generate migration create_lesson_topic
```

10. Inside the `create_table` block, add associations to topics and lessons with `t.references :topic` and `t.references :lesson`

```ruby
    bin/rails generate migration CreateLessonTopics topic:references lesson:references
```

- `models/lesson_topic.rb`

```ruby
    class LessonTopic < ApplicationRecord
        belongs_to :topic
        belongs_to :lesson
    end
```

11. Run the migration.
12. If the migration run was successful, create the model for your join table (be sure the name matches Rails conventions).
13. Open the console and test your new models by creating the topics above and adding them to some lessons.

```ruby
    Topic.create(
        title: "SQL",
        description: "SQL (Structured Query Language) is a standardized language used to manage and manipulate relational databases. It allows users to perform tasks such as querying data, inserting new records, updating existing ones, and deleting data. SQL is also used to create and modify the structure of database tables and to control access to data. Common SQL commands include SELECT, INSERT, UPDATE, DELETE, CREATE, and DROP.")

    Topic.create(
        title: "Data Modeling",
        description: "Data modeling is the process of creating a visual representation of how data is organized and related within a system. It helps define the structure, relationships, and rules of data, making it easier to design databases and ensure data consistency. Data models typically include entities (like people or products), attributes (details about entities), and relationships (how entities are connected). It’s an essential step in database design, supporting both technical implementation and clear communication between stakeholders.")

    Topic.create(
        title: "Javascript",
        description: "JavaScript is a versatile, high-level programming language primarily used to create interactive and dynamic content on websites. It runs in web browsers and allows developers to implement features like image sliders, form validation, animations, and real-time updates without needing to reload the page. JavaScript can also be used on the server side (with environments like Node.js), making it a full-stack language. It's an essential part of the web development trio, alongside HTML and CSS.")

    Topic.create(
        title: "Automated Testing",
        description: "Automated testing is the process of using software tools to run tests on applications automatically, without manual intervention. It helps ensure that code works as expected by checking functionality, performance, and reliability. Automated tests can run quickly and repeatedly, making them ideal for catching bugs early, especially during continuous integration and deployment. Common types include unit tests, integration tests, and end-to-end tests.")

    Topic.create(
        title: "Debugging",
        description: "Debugging is the process of identifying, analyzing, and fixing bugs or errors in software code. It involves examining the code, running tests, and using tools to trace and resolve issues that cause incorrect behavior or crashes. Debugging helps ensure the software functions correctly and efficiently.")

    Topic.create(
        title: "Web Request Cycle",
        description: "The web request cycle is the process that happens when a user interacts with a website, typically by entering a URL or clicking a link. 1. Request: The user’s browser sends an HTTP request to the web server. 2. Processing: The server receives the request, processes it (often interacting with a database), and prepares a response. 3. Response: The server sends back an HTTP response, usually containing HTML, CSS, and JavaScript. 4. Rendering: The browser receives the response and renders the webpage for the user to see and interact with. This cycle happens quickly and repeats with each user action that triggers a new request.")

    Topic.create(
        title: "HTTP",
        description: "HTTP (Hypertext Transfer Protocol) is the foundation of data communication on the web. It defines how messages are formatted and transmitted between clients (like web browsers) and servers. When you visit a website, your browser sends an HTTP request to the server, which then responds with the requested resources, such as HTML pages, images, or data. HTTP is a stateless protocol, meaning each request is independent and doesn't retain information from previous interactions.")

    LessonTopic.create(lesson_id: 211, topic_id: 1)
    LessonTopic.create(lesson_id: 212, topic_id: 2)
    LessonTopic.create(lesson_id: 201, topic_id: 3)
    LessonTopic.create(lesson_id: 214, topic_id: 4)
    LessonTopic.create(lesson_id: 215, topic_id: 5)
    LessonTopic.create(lesson_id: 202, topic_id: 6)
    LessonTopic.create(lesson_id: 202, topic_id: 7)

```
