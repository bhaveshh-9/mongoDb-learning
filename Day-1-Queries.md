1. Show Databases

show dbs

Meaning: Show databases.

Description: Lists databases that contain stored data.

2. Select a Database

use collegeDB

Meaning: Switch to the collegeDB database.

Description: Selects the database where you want to run commands. MongoDB creates it when data is first stored if it does not already exist.

3. Show Collections

show collections

Meaning: Show collections.

Description: Lists the collections in the currently selected database.

4. Find All Students

db.student.find()

Meaning: Find all documents.

Description: Retrieves all student documents from the student collection.

5. Find One Student

db.student.findOne()

Meaning: Find one document.

Description: Returns one student document from the collection.

6. Find Students by City

db.student.find({ city: "Jalgaon" })

Meaning: Filter students by city.

Description: Returns students whose city field equals "Jalgaon".

7. Find Students with Fees Greater Than 40000

db.student.find({ fees: { $gt: 40000 } })

Meaning: Find students whose fees are greater than 40000.

Description: The $gt comparison operator matches documents where fees is greater than 40000.

8. Update One Student

db.student.updateOne(
  { city: "Jalgaon" },
  { $set: { name: "Bhavesh Atmaram Patil" } }
)

Meaning: Update one matching student.

Description:

{ city: "Jalgaon" } is the filter used to find a student.

$set changes the specified field.

updateOne() updates only the first document that matches the filter.

Note: If multiple students live in Jalgaon, this query updates only one of them.

9. Verify a Student's Updated Data

db.student.findOne({ city: "Jalgaon" })

Meaning: Find one student from Jalgaon.

Description: Returns one matching document so you can inspect its current values.

10. Insert One Student

db.student.insertOne({
  name: "Practice Student",
  city: "Pune",
  fees: 35000
})

Meaning: Insert one document.

Description: Adds a new student document with the specified fields. Use this example only if these fields fit your collection's structure.

11. Insert Multiple Students

db.student.insertMany([
  { name: "Student A", city: "Pune", fees: 30000 },
  { name: "Student B", city: "Nashik", fees: 45000 }
])

Meaning: Insert multiple documents.

Description: Adds multiple student documents in one operation. These are practice examples; avoid inserting them if you do not want duplicate or sample records in your collection.

12. Delete One Student

db.student.deleteOne({ name: "Practice Student" })

Meaning: Delete one matching document.

Description: Deletes the first document matching the filter. Use this only for a practice record you intend to remove.
