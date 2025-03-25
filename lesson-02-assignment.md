# LESSON 02 ASSIGNMENT
by Annie Kwon
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
#### Stardew Valley Love Journal
The users are the gamers who like to play Stardew Valley and want to keep journal of their activities in the game. There is one type of user. 
The main feature is the player keep tabs on the marriage candidate villagers with heart levels, if they're dating, their list of likes and dislikes.
- A user can add an item to a list. There are multiple lists. 
- A user can see how many hearts that they currently have with the villagers. 
- A user can add a dating status to a villager. 

### Question 4 - Design the data model for your project
**Models**
- Villager
  - name
  - dating?
  - heart_level
  - gender
  - address
  - id
- Item
  - name
  - category
  - love
  - id
  - villager_id
  - points_id
- Point
  - love
  - like
  - dislike
  - hate
  - id