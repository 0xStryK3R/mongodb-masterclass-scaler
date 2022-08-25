1. Count no. of documents: `countDocuments`
    ```mongodb
    db.collection.countDocuments({});
    ```

2. Find Documents (Optional - conditions): `find`
    ```mongodb
    db.collection.find({});
    ```

3. `AND` Operator: `$and`
    ```mongodb
    db.collection.find({
    $and: [
        {
        capital: "Washington, D.C."
        },
        {
        name: "United States"
        }
    ]
    })
    ```


4. `OR` Operator: `$or`
    ```mongodb
    db.collection.find({
    $or: [
        {
        capital: "Washington, D.C."
        },
        {
        capital: "canberra"
        }
    ]
    })
    ```

5. `IN` Operator: `$in`
    ```mongodb
    db.collection.find({
    $or: [
        {
        capital: "Washington, D.C."
        },
        {
        population: {
            $in: [
            125960000,
            210147125
            ]
        }
        }
    ]
    })
    ```

6. `Lesser Than` Operator: `$lt`
    ```mongodb
    db.collection.find({
    $or: [
        {
        population: {
            $lt: 328239523
        }
        },
        {
        population: {
            $lt: [
            125960000,
            210147125
            ]
        }
        }
    ]
    })
    ```

7. `Greater Than` Operator: `$gt`
    ```mongodb
    db.collection.find({
    $or: [
        {
        population: {
            $gt: 328239523
        }
        },
        {
        population: {
            $in: [
            125960000,
            210147125
            ]
        }
        }
    ]
    })
    ```

8. `Equal To` Operator: `$eq`
    ```mongodb
    db.collection.find({
    $or: [
        {
        name: {
            $eq: "Australia"
        }
        },
        {
        population: {
            $in: [
            125960000,
            210147125
            ]
        }
        }
    ]
    })
    ```

9. `Not Equal To` Operator: `$ne`
    ```mongodb
    db.collection.find({
    $or: [
        {
        name: {
            $eq: "Australia"
        }
        },
        {
        name: {
            $ne: "United States"
        }
        }
    ]
    })
    ```

10. `NOT IN` Operator: `$nin`
    ```mongodb
    db.collection.find({
    $or: [
        {
        capital: "Washington, D.C."
        },
        {
        population: {
            $nin: [
                125960000,
                210147125
            ]
        }
        }
    ]
    })
    ```

11. `Greater Than Or Equal To` Operator: `$gte`
    ```mongodb
    db.collection.find({
    population: {
        $gte: 125960000
    }
    })
    ```

12. `Lesser Equal To Than` Operator: `$lte`
    ```mongodb
    db.collection.find({
    population: {
        $lte: 125960000
    }
    })
    ```

13. `Nor` Operator: `$nor`
    ```mongodb
    db.collection.find({
    $nor: [
        {
        population: 210147125
        },
        {
        population: 125960000
        }
    ]
    })
    ```

14. `Exists` Operator: `$exists`
    db.collection.find({
    population: {
        $exists: true,
        $nin: [
        210147125,
        125960000
        ]
    }
    })
    ```

