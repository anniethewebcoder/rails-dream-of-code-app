# Question 1

```ruby

    spring2026 = Trimester.find_by(year: 2026, term: 'Spring')
    spring2026_id = spring2026.id

    coding_classes = CodingClass.all

    coding_classes.each do | coding_class |
        Course.create(
            coding_class_id: coding_class.id,
            trimester_id: spring2026_id,
            max_enrollment: 25
        )
    end

```

# Question 2

```ruby
    spring2026 = Trimester.find_by(year: 2026, term: 'Spring')
    spring2026_id = spring2026.id

    new_student = Student.create(
        first_name: 'Cody',
        last_name: 'Gram',
        email: 'procodygram@email.com'
    )
    new_student_id = new_student.id

    intro_class = CodingClass.find_by(title: 'Intro to Programming')
    intro_class_id = intro_class.id

    spring2026_course = Course.find_by(trimester_id: spring2026_id, coding_class_id: intro_class_id)
    spring2026_course_id = spring2026_course

    new_enrollment = Enrollment.create(
        course_id: spring2026_course_id,
        student_id: new_student_id
    )
    new_enrollment_id = new_enrollment.id

    assigned_mentor = MentorEnrollmentAssignment.select('mentor_id').group('mentor_id').having('count(mentor_id) < ?', 3)
    assigned_mentor_id = assigned_mentor[0].mentor_id

    MentorEnrollmentAssignment.create(
        mentor_id: assigned_mentor_id,
        enrollment_id: new_enrollment_id
    )
```

# Question 3

It's a quiz maker for teachers and quiz taker for students. It's like Quizlet except it's purely quiz.

- A user (teacher) can add questions and answers.
- A user (student) can select answer to each question.
- A user (teacher) can see the results of the selected student's quiz.
- A user (teacher) can see the average of the student and the class.

# Question 4

Still thinking about it.
