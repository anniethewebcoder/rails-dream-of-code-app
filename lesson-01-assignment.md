# Question 1

```ruby

intro_prog = CodingClass.find_by({ title: 'Intro to Programming' })
intro_prog_id = intro_prog.id

spring_2025 = Trimester.find_by({ year: 2025, term: 'Spring' })
spring_2025_id = spring_2025.id

course_intro_spring_2025 = Course.find_by({ coding_class: intro_prog_id, trimester_id: spring_2025_id })
course_intro_spring_2025_id = course_intro_spring_2025.id

Enrollment.where(course_id: course_intro_spring_2025_id).limit(2).each do |enrollment|
    student = Student.find_by(id: enrollment.student_id)
    puts "%d, %s" % [student.id, student.email]
end

```

# Question 2

```ruby

intro_prog = CodingClass.find_by({ title: 'Intro to Programming' })
intro_prog_id = intro_prog.id

spring_2025 = Trimester.find_by({ year: 2025, term: 'Spring' })
spring_2025_id = spring_2025.id

course_intro_spring_2025 = Course.find_by({ coding_class: intro_prog_id, trimester_id: spring_2025_id })
course_intro_spring_2025_id = course_intro_spring_2025.id

enrollments_nil = Enrollment.where({ course_id: course_intro_spring_2025_id, final_grade: nil })

enrollments_nil.each do |enrollment|
    mentor_enroll = MentorEnrollmentAssignment.find_by(enrollment_id: enrollment.id)
    mentor_id = mentor_enroll.mentor_id
    mentor = Mentor.find_by(id: mentor_id)
    mentor_email = mentor.email
    puts "%d, %s" % [mentor_id, mentor_email]
end

```
