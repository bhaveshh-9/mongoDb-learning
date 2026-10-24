MONGODB DAY 3 — AGGREGATION QUERIES

Note:
These queries use the student collection and assume fields such as name, course, marks, and fees exist in your documents.

----------------------------------------
1. Count Students in Each Course
----------------------------------------

db.student.aggregate([
  {
    $group: {
      _id: "$course",
      totalCount: { $sum: 1 }
    }
  }
])

----------------------------------------
2. Calculate Average Marks by Course
----------------------------------------

db.student.aggregate([
  {
    $group: {
      _id: "$course",
      avgMarks: { $avg: "$marks" }
    }
  }
])

----------------------------------------
3. Find Students Belonging to IT
----------------------------------------

db.student.aggregate([
  {
    $match: {
      course: "IT"
    }
  }
])

----------------------------------------
4. Sort Students by Marks in Descending Order
----------------------------------------

db.student.aggregate([
  {
    $sort: {
      marks: -1
    }
  }
])

----------------------------------------
5. Display Only Name and Marks
----------------------------------------

db.student.aggregate([
  {
    $project: {
      _id: 0,
      name: 1,
      marks: 1
    }
  }
])

----------------------------------------
6. Find Top 3 Students by Marks
----------------------------------------

db.student.aggregate([
  {
    $sort: {
      marks: -1
    }
  },
  {
    $limit: 3
  },
  {
    $project: {
      _id: 0,
      name: 1,
      marks: 1
    }
  }
])

----------------------------------------
7. Find Top 3 Students in IT
----------------------------------------

db.student.aggregate([
  {
    $match: {
      course: "IT"
    }
  },
  {
    $sort: {
      marks: -1
    }
  },
  {
    $limit: 3
  },
  {
    $project: {
      _id: 0,
      name: 1,
      course: 1,
      marks: 1
    }
  }
])

----------------------------------------
8. Calculate Total Fees by Course
----------------------------------------

db.student.aggregate([
  {
    $group: {
      _id: "$course",
      totalFees: { $sum: "$fees" }
    }
  }
])

----------------------------------------
9. Count Students in Each City
----------------------------------------

db.student.aggregate([
  {
    $group: {
      _id: "$city",
      totalStudents: { $sum: 1 }
    }
  }
])

----------------------------------------
10. Show Only IT Students with Their Marks,
    Sorted by Marks in Descending Order
----------------------------------------

db.student.aggregate([
  {
    $match: {
      course: "IT"
    }
  },
  {
    $project: {
      _id: 0,
      name: 1,
      marks: 1
    }
  },
  {
    $sort: {
      marks: -1
    }
  }
])

----------------------------------------
END OF DAY 3 QUERIES
----------------------------------------
