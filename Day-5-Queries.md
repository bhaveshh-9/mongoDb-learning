MongoDB Day 5 - Practice Queries with Answers

==================================================

Sample Data

==================================================

Students Collection

db.students.insertMany([
  {
    _id: 101,
    name: "Rahul",
    courseId: 501,
    address: { city: "Pune", state: "Maharashtra" },
    skills: ["Java", "MongoDB", "Angular"]
  },
  {
    _id: 102,
    name: "Amit",
    courseId: 502,
    address: { city: "Mumbai", state: "Maharashtra" },
    skills: ["Python", "MongoDB"]
  },
  {
    _id: 103,
    name: "Priya",
    courseId: 501,
    address: { city: "Pune", state: "Maharashtra" },
    skills: ["Java", "Spring Boot"]
  },
  {
    _id: 104,
    name: "Sneha",
    courseId: 503,
    address: { city: "Delhi", state: "Delhi" },
    skills: ["Angular", "Python"]
  }
])

Courses Collection

db.courses.insertMany([
  { _id: 501, courseName: "MCA" },
  { _id: 502, courseName: "MBA" },
  { _id: 503, courseName: "BCA" }
])

NOTE: Sample data ko sirf ek baar insert karna. Dobara run karne par duplicate _id error aa sakta hai.

==================================================

Q1. Find students who live in Pune.

==================================================

db.students.find({ "address.city": "Pune" })

==================================================

Q2. Find students who belong to Maharashtra.

==================================================

db.students.find({ "address.state": "Maharashtra" })

==================================================

Q3. Find students who have MongoDB in their skills.

==================================================

db.students.find({ skills: "MongoDB" })

==================================================

Q4. Find students who have both Java and MongoDB skills.

==================================================

db.students.find({
  skills: { $all: ["Java", "MongoDB"] }
})

==================================================

Q5. Add Docker to Rahul's skills using $push.

==================================================

db.students.updateOne(
  { name: "Rahul" },
  { $push: { skills: "Docker" } }
)

==================================================

Q6. Add MongoDB to Priya's skills using $addToSet.

==================================================

db.students.updateOne(
  { name: "Priya" },
  { $addToSet: { skills: "MongoDB" } }
)

==================================================

Q7. Remove Python from Amit's skills using $pull.

==================================================

db.students.updateOne(
  { name: "Amit" },
  { $pull: { skills: "Python" } }
)

==================================================

Q8. Change Rahul's city from Pune to Bangalore.

==================================================

db.students.updateOne(
  { name: "Rahul" },
  { $set: { "address.city": "Bangalore" } }
)

==================================================

Q9. Find students who live in Pune and have Java as a skill.

==================================================

db.students.find({
  "address.city": "Pune",
  skills: "Java"
})

==================================================

Q10. Find Rahul's course using a reference.

==================================================

Step 1: Find the student.

db.students.findOne({ _id: 101 })

Step 2: Use the student's courseId to find the course.

db.courses.findOne({ _id: 501 })

==================================================

Q11. Use $lookup to combine students and courses.

==================================================

db.students.aggregate([
  {
    $lookup: {
      from: "courses",
      localField: "courseId",
      foreignField: "_id",
      as: "courseDetails"
    }
  }
])

==================================================

Q12. Display each student's name and course details.

==================================================

db.students.aggregate([
  {
    $lookup: {
      from: "courses",
      localField: "courseId",
      foreignField: "_id",
      as: "courseDetails"
    }
  },
  {
    $project: {
      _id: 0,
      name: 1,
      courseDetails: 1
    }
  }
])

==================================================

Q13. Find students enrolled in the MCA course using $lookup.

==================================================

db.students.aggregate([
  {
    $lookup: {
      from: "courses",
      localField: "courseId",
      foreignField: "_id",
      as: "courseDetails"
    }
  },
  {
    $match: {
      "courseDetails.courseName": "MCA"
    }
  }
])

==================================================

Q14. What happens if a student has courseId 999 and no matching course exists?

==================================================

The courseDetails field will be an empty array: [].

Example:

db.students.aggregate([
  {
    $lookup: {
      from: "courses",
      localField: "courseId",
      foreignField: "_id",
      as: "courseDetails"
    }
  }
])

If a student's courseId does not match any course _id, that student's courseDetails array will be empty.

==================================================

Q15. Should address be embedded or stored separately?

==================================================

Answer:

An address can be embedded inside the student document because city and state are closely related to the student and are often accessed together.

Example:

{
  name: "Rahul",
  address: {
    city: "Pune",
    state: "Maharashtra"
  }
}

A separate collection may be better when address information is large, independently managed, or shared by multiple documents.

==================================================

Day 5 Completed

==================================================
