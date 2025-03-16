# LESSON 01 ASSIGNMENT

#### by Annie Kwon

## Question 1

### Finish Task 1: Collect emails for students in the current intro course

```ruby
coding_class_id = CodingClass.find_by({ title: 'Intro to Programming' }).id
trimester_id = Trimester.find_by({ year: 2025, term: 'Spring' }).id
course_id = Course.find_by({ coding_class_id: coding_class_id, trimester_id: trimester.id }).id

Enrollment.where(course_id: course_id).limit(2).each do | enrollment |
    student = Student.find_by( id: enrollment.student_id)
    puts "%d, %s" % [student.id, student.email]
end
```

## Question 2

### Task 2: Emall all mentors who have not assigned a final grade

```ruby
coding_class_id = CodingClass.find_by({ title: 'Intro to Programming' }).id
trimester_id = Trimester.find_by({ year: 2025, term: 'Spring' }).id
course_id = Course.find_by({ coding_class_id: coding_class_id, trimester_id: trimester.id }).id

enrollment_ids = Enrollment.where({ course_id: course_id, final_grade: nil}).id

enrollments_id.each do | enrollment |
    mentor_id = MentorEnrollmentAssignment.find_by(enrollment_id: enrollment.id).mentor_id
    mentor_email = Mentor.find_by( id: mentor_id ).email
    puts "%d, %s" % [mentor_id, mentor_email]
end
```
