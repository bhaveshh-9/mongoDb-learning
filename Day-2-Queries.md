DAY 2 — MONGODB QUERY OPERATORS

----------------------------------------

TOPIC 1: $gt (GREATER THAN)

Meaning:
Greater than.

Query:
db.student.find({ fees: { $gt: 40000 } })

Description:
Returns students whose fees are greater than 40000.

----------------------------------------

TOPIC 2: $gte (GREATER THAN OR EQUAL)

Meaning:
Greater than or equal to.

Query:
db.student.find({ fees: { $gte: 40000 } })

Description:
Returns students whose fees are greater than or equal to 40000.

----------------------------------------

TOPIC 3: $lt (LESS THAN)

Meaning:
Less than.

Query:
db.student.find({ fees: { $lt: 40000 } })

Description:
Returns students whose fees are less than 40000.

----------------------------------------

TOPIC 4: $lte (LESS THAN OR EQUAL)

Meaning:
Less than or equal to.

Query:
db.student.find({ fees: { $lte: 40000 } })

Description:
Returns students whose fees are less than or equal to 40000.

----------------------------------------

TOPIC 5: $ne (NOT EQUAL)

Meaning:
Not equal to.

Query:
db.student.find({ city: { $ne: "Jalgaon" } })

Description:
Returns students whose city is not Jalgaon. Documents without a city field may also match.

----------------------------------------

TOPIC 6: $in (MATCH ANY VALUE)

Meaning:
Matches any value from a specified list.

Query:
db.student.find({
  city: { $in: ["Jalgaon", "Pune"] }
})

Description:
Returns students whose city is either Jalgaon or Pune.

----------------------------------------

TOPIC 7: $and (AND OPERATOR)

Meaning:
All conditions must be true.

Query:
db.student.find({
  $and: [
    { marks: { $gt: 80 } },
    { course: "IT" }
  ]
})

Description:
Returns students who have marks greater than 80 AND whose course is IT.

----------------------------------------

TOPIC 8: $or (OR OPERATOR)

Meaning:
At least one condition must be true.

Query:
db.student.find({
  $or: [
    { city: "Jalgaon" },
    { fees: { $gt: 40000 } }
  ]
})

Description:
Returns students who live in Jalgaon OR whose fees are greater than 40000. Both conditions may also be true.

----------------------------------------

TOPIC 9: MULTIPLE CONDITIONS WITHOUT $and

Query:
db.student.find({
  marks: { $gt: 80 },
  course: "IT"
})

Description:
Returns students whose marks are greater than 80 and whose course is IT.

Note:
When multiple fields are specified in the same query object, MongoDB applies AND logic.

----------------------------------------

TOPIC 10: $and VS $or

$and:
All specified conditions must match.

$or:
At least one specified condition must match.

----------------------------------------
