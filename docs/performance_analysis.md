📈 Performance Analysis Report
This document analyzes the performance improvements and execution strategies of selected MongoDB queries, enhanced through appropriate indexing. The analysis is based on query execution time and the output of the explain() method.

🔍 1. Find User by Email
Query: db.users.find({"email": "alice.johnson@example.com"})

Index Used: email_1

Execution Time: 0.000122 seconds

Winning Plan: IXSCAN (Index Scan on email)

Explain Summary:

MongoDB successfully utilized a single-field ascending index on the email field.

The IXSCAN plan indicates the query was able to directly navigate the B-tree index without scanning the collection.

There were no rejected plans, and the plan cache key was efficiently computed.

✅ Conclusion: This query was significantly optimized by indexing. Without the index, MongoDB would have performed a collection scan (COLLSCAN), which is far slower on large datasets.


🔍 2. Search Courses by Title and Category
Query:
db.courses.find({
  "$text": { "$search": "Data" },
  "category": "Engineering"
})

Index Used: title_text_category_1 (compound index with text and ascending field)

Execution Time: 0.000084 seconds

Winning Plan: TEXT_MATCH + IXSCAN (text search plus index scan)

Explain Summary:

The compound index included a text index on title and a regular index on category.

MongoDB used a TEXT_MATCH stage for efficient full-text search, followed by an IXSCAN on the filtered category field.

Query planner determined the most optimal path with no rejected plans, indicating excellent index coverage.

✅ Conclusion: The query was extremely efficient due to the combined use of text search and category filtering within a compound index. This approach drastically reduced execution time and allowed indexed filtering instead of document-level scanning.

🔍 3. Assignments Due in the Next 7 Days
Query:
db.assignments.find({
  "dueDate": {
    "$gte": ISODate("2025-06-16T22:21:22Z"),
    "$lte": ISODate("2025-06-23T22:21:22Z")
  }
})

Index Used: dueDate_1

Execution Time: 0.000077 seconds

Winning Plan: IXSCAN on dueDate

Explain Summary:

A range scan was performed using an ascending index on the dueDate field.

The IXSCAN strategy allowed MongoDB to quickly locate matching documents within the specified date window.

The input stage filtered dates using the index bounds, which ensured optimal query execution.

✅ Conclusion: By indexing dueDate, this range-based date query was optimized to avoid scanning the full assignments collection. The index bounds were utilized efficiently for a time-based filter.

🧠 Overall Summary
| Query Description                | Index Used              | Time Taken (s) | Query Strategy          |
| -------------------------------- | ----------------------- | -------------- | ----------------------- |
| Find user by email               | `email_1`               | 0.000122       | `IXSCAN`                |
| Search courses by title/category | `title_text_category_1` | 0.000084       | `TEXT_MATCH` + `IXSCAN` |
| Assignments due next 7 days      | `dueDate_1`             | 0.000077       | `IXSCAN`                |

Each query was significantly improved with appropriate indexing. Execution times remained well below 0.001 seconds, demonstrating MongoDB’s efficiency when indexes are properly designed for common access patterns.