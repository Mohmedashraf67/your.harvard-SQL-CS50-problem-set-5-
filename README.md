# Harvard Course Database Optimization

## Problem and Solution Overview

### Problem to Solve

Harvard's course shopping tool, my.harvard, allows students to explore and register for classes. This tool relies on an underlying database to manage courses, students, and their registrations. However, the tool is known for being slow, negatively affecting user experience.

To address this issue, I was tasked with optimizing the database by creating indexes to speed up typical queries. The objective was to balance speed with disk space, ensuring the most efficient representation of Harvard’s courses and students.

### How I Used My Database Skills to Solve It

To improve the performance of my.harvard, I implemented the following database optimization strategies:

1. **Identifying Typical Queries**:
   - **Problem**: Determining which queries are most frequently run on the database to understand where performance improvements are needed.
   - **Solution**: I analyzed typical SELECT queries to identify the most commonly accessed columns and tables, which helped in deciding where to create indexes.

2. **Creating Indexes**:
   - **Problem**: Selecting columns for indexing to enhance query performance without excessively increasing disk space usage.
   - **Solution**: By using the `EXPLAIN QUERY PLAN` command, I evaluated the performance of each query. I then created indexes on columns that were frequently used in WHERE clauses and JOIN operations, significantly improving query response times.

3. **Balancing Speed and Disk Space**:
   - **Problem**: Avoiding the creation of unnecessary indexes that could lead to excessive disk space consumption.
   - **Solution**: I focused on minimizing the number of indexes by only indexing columns that provided a substantial improvement in query performance. This balance ensured efficient use of disk space while enhancing the overall speed of the database.

### Specific Solutions Implemented

1. **Index on Student Table**:
   - **Problem**: Queries frequently filtered or joined on student IDs.
   - **Solution**: I created an index on the `student_id` column to speed up these operations.

2. **Index on Course Table**:
   - **Problem**: Course-related queries often used course IDs in their filtering criteria.
   - **Solution**: I created an index on the `course_id` column to improve the performance of these queries.

3. **Index on Enrollment Table**:
   - **Problem**: Enrollment-related queries typically involved student IDs and course IDs.
   - **Solution**: I created composite indexes on the `student_id` and `course_id` columns to enhance the efficiency of enrollment queries.

4. **Index on Requirements Table**:
   - **Problem**: Queries frequently accessed requirement IDs.
   - **Solution**: I created an index on the `requirement_id` column to speed up these queries.

5. **Index on Satisfies Table**:
   - **Problem**: Queries often joined this table on both student IDs and requirement IDs.
   - **Solution**: I created composite indexes on the relevant columns to optimize these join operations.

### Conclusion

By analyzing the typical queries and strategically creating indexes, I was able to significantly improve the performance of the my.harvard database. These optimizations ensured that the system could handle typical queries more efficiently, providing a faster and smoother experience for users. This approach not only solved the immediate performance issues but also contributed to a more scalable and maintainable database system.
