# LESSON 02 ASSIGNMENT

To submit your answers, add a file to the root directory of your `rails-dream-of-code` app called `lesson-02-assignment`. Include your answers in that file, commit the file and make a pull request on your fork of the project (double-check your pull request is not based on the main Code the Dream project). Submit the pull request link with your assignment submission.

### Question 1
```Ruby
Trimester.create(
  year: '2026', 
  term: 'Spring', 
  application_deadline: '2026-02-15', 
  start_date: "2026-03-01", 
  end_date: "2026-06-30"
)

spring2026_id = Trimester.find_by(year: 2026, term: 'Spring').id

coding_classes = CodingClass.all

coding_classes.each do | coding_class |
  Course.create(
    coding_class_id: coding_class.id,
    trimester_id: spring2026_id,
    max_enrollment: 25,
  )
end
```

### Question 2
```Ruby
new_student = Student.create(
  first_name: 'Annie',
  last_name: 'Kwon',
  email: 'anniekwon@email.com'
)

spring2026_trimester_id = Trimester.find_by(year: 2026, term: "Spring").id
intro_class_id = CodingClass.find_by(title: 'Intro to Programming').id

spring2026_course_id = Course.find_by(trimester_id: spring2026_trimester_id, coding_class_id: intro_class_id).id

new_enrollment = Enrollment.create(
  course_id: spring2026_course_id,
  student_id: new_student.id   
)

assigned_mentor = MentorEnrollmentAssignment.select("mentor_id").group("mentor_id").having("count(mentor_id) < ?", 2)
assigned_mentor_id = assigned_mentor[0].mentor_id

MentorEnrollmentAssignment.create(
  mentor_id: assigned_mentor_id,
  enrollment_id: new_enrollment.id,
)
```

### Question 3 - Describe your project
Let's begin designing the data model for your project! We'll need to start with a high level description of the application and what a user should be able to do in the app.

Write a description of your project idea. Try to answer the questions below in your description if they are applicable.
- Who are the users of your application? Do you have different types of users or different roles?
- What are the core user scenarios or features of your app? These could be statements like...
    - "A user can create book reviews"
    - "A user can add books to their bookshelf"
    - "A user can like view the book reviews of another user"
- Or if it makes more sense for your idea, you might describe some process or flow...for example:
    - "First, a meeting organizer creates a poll. Then they add meeting attendees, and the attendees vote on a time. Then after each has voted, the poll closes and a meeting is created."
- Consider sketching some wireframes for the main or more complex screens of your app. When you do this, think of what data you'll need to display on each page.

Write your description in the `lesson-02-assignment` file.

### Question 4 - Design the data model for your project
1. Start by just listing out what you think the "nouns" or tables (or models) will be in your application. What are the things you talk about when you describe the application?
2. Now think about the data each of these things will hold. Some of these may be attributes or columns, but be on the lookout for data that may be associations with other "nouns".
3. Create an ERD to visualize your tables and data.
    1. Don't worry too much about following ERD creation rules exactly. Just list table names and column names.
    2. **Do** try to follow Rails naming conventions here. If you figure this out now and note them in your ERD or your plan, it will be easier for you when creating your migrations and models.
    3. Do your best, but know that this is a starting point for collaboration between you and your mentors. When designing a data model on a software team, often more than one developer collaborate on the design together. You should plan to iterate on your design and expect feedback and input from your mentors.

You can either create a text-based ERD, just indicating table names and column names, or you can use a drawing tool and include a jpg or pdf in the root of your project. If you include the ERD just as text, you can include it in `lesson-02-assignment`. For a pdf or jpg (or any other image), name your file `lesson-02-erd` and include it in the root of your project.
