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

| topic |
| ------ |
| **id**: integer, primary key |
| **title**: string |
| **description**: text |

| lesson_topic |
| ------------ |
| **id**: integer, primary key |
| **lesson_id**: integer, foreign key |
| **topic_id**: intger, foreign key |

5. Determine the generator command you'll need to create the migration file and run the command to generate the empty migration file. **Start with just the topics migration.** (Hint: your filename should be `create_topics`)

```ruby
    bin/rails generate migration create_topics
```
6. Inside the `create_table` block in the migration file, add the appropriate columns and datatypes.

```ruby
    bin/rails generate migration CreateTopics title:string description:text
```
  
7. Run the migration with `bin/rails db:migrate` (in a terminal window, not a rails console). Watch the output and make sure it is successful before moving on. (You can check the database to see if your table exists.)

8. Add the `Topic` model before moving on.
9. Now determine the generator command you'll need to create the migration file for the join table. Don't forget that it should begin with `create_` and be followed by the table name.
10. Inside the `create_table` block, add associations to topics and lessons with `t.references :topic` and `t.references :lesson`
11. Run the migration.
12. If the migration run was successful, create the model for your join table (be sure the name matches Rails conventions).
13. Open the console and test your new models by creating the topics above and adding them to some lessons.

Commit all modified and created files and create a PR to submit for your assignment.

Here are the topic titles that we'll need to store:
- SQL
- Data Modeling
- Javascript
- CSS
- Automated Testing
- Debugging
- Web Request Cycle
- HTTP