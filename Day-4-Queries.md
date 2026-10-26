Q1. Create an Ascending Index on name

db.student.createIndex({ name: 1 })

Q2. Display All Indexes

db.student.getIndexes()

Q3. Drop the name_1 Index

db.student.dropIndex("name_1")

Q4. Create a Descending Index on city

db.student.createIndex({ city: -1 })

Q5. Create a Compound Index on course and marks

db.student.createIndex({ course: 1, marks: -1 })

Q6. Create a Unique Index on email

db.student.createIndex({ email: 1 }, { unique: true })

Q7. Check Query Execution using explain()

db.student.find({ name: "Rahul" }).explain("executionStats")

Q8. Understand COLLSCAN and IXSCAN

COLLSCAN: MongoDB scans documents in the collection to find matching results.

IXSCAN: MongoDB scans an index to help find matching results.

Q9. Create a Capped Collection

db.createCollection("logs", {
  capped: true,
  size: 5000
})

Q10. Insert Documents into logs

db.logs.insertOne({ message: "Server started" })

db.logs.insertOne({ message: "User logged in" })

