## Count Documents | [Dataset 1](/Datasets/1.txt)

1. Count no. of documents: `countDocuments`
    ```mongodb
    db.collection.countDocuments({});
    ```

## Find Queries | [Dataset 1](/Datasets/1.txt)

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


4. `OR` Operator: `$or` | [Dataset 1](/Datasets/1.txt)
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

5. `IN` Operator: `$in` | [Dataset 1](/Datasets/1.txt)
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

6. `Lesser Than` Operator: `$lt` | [Dataset 1](/Datasets/1.txt)
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

7. `Greater Than` Operator: `$gt` | [Dataset 1](/Datasets/1.txt)
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

8. `Equal To` Operator: `$eq` | [Dataset 1](/Datasets/1.txt)
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

9. `Not Equal To` Operator: `$ne` | [Dataset 1](/Datasets/1.txt)
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

10. `NOT IN` Operator: `$nin` | [Dataset 1](/Datasets/1.txt)
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

11. `Greater Than Or Equal To` Operator: `$gte` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
    db.collection.find({
    population: {
        $gte: 125960000
    }
    })
    ```

12. `Lesser Equal To Than` Operator: `$lte` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
    db.collection.find({
    population: {
        $lte: 125960000
    }
    })
    ```

13. `Nor` Operator: `$nor` | [Dataset 1](/Datasets/1.txt)
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

14. `Exists` Operator: `$exists` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
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

## Update Queries

15. U[date Query with `Set` Operator: `set` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
    db.collection.update({
    _id: "62e5288f4d0440f7811d1928"
    },
    {
    $set: {
        "capital": "Dubai",
        "language": "arabic",
        "name": "UAE"
    }
    })

    ```
    

16. Rename: `$rename` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
    db.collection.update({
    _id: "62e5288f4d0440f7811d1928"
    },
    {
    $rename: {
        "capital": "Capital City",
        "continent": "Kontinent"
    }
    })

    ```
    

17. `Inc` Operator: `$inc` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
    db.collection.update({
    name: "United States"
    },
    {
    $inc: {
        population: 2
    }
    })

    ```
    

18. `Min` Operator: `$min` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
    db.collection.update({
    name: "United States"
    },
    {
    $min: {
        population: 20
    }
    })

    ```
    

19. `Max` Operator: `$max` | [Dataset 1](/Datasets/1.txt)
    db.collection.update({
    name: "United States"
    },
    {
    $max: {
        population: 428239523
    }
    })
    ```mongodb
    ```
    

20. `Mul` Operator: `$mul` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
    db.collection.update({
    name: "United States"
    },
    {
    $mul: {
        population: 2
    }
    })
    ```
    

21. `Unset` Operator: `$unset` | [Dataset 1](/Datasets/1.txt)
    ```mongodb
    db.collection.update({
    name: "United States"
    },
    {
    $unset: {
        capital: "",
        continent: ""
    }
    })
    ```

## Array Operations
    
22. `$` Operator: | [Dataset 2](/Datasets/2.txt)
    ```mongodb
    db.collection.update({
    _id: 1,
    grades: 80,
    
    },
    {
    $set: {
        "grades.$": 82
    }
    })
    ```
    
23. `Dot` Operator: `$.` | [Dataset 3](/Datasets/3.txt)
    ```mongodb
    db.collection.update({
    _id: 4,
    "grades.grade": 80,
    
    },
    {
    $set: {
        "grades.$.std": 6
    }
    })
    ```
    
24. `$elemMatch`: | [Dataset 3](/Datasets/3.txt)
    ```mongodb
    db.collection.update({
    _id: 4,
    grades: {
        $elemMatch: {
        grade: {
            $lte: 90
        },
        mean: {
            $gt: 80
        }
        }
    }
    },
    {
    $set: {
        "grades.$.std": 6
    }
    })
    ```
    
24. Embedded data: | [Dataset 4](/Datasets/4.txt)
    ```mongodb
    db.collection.find({
    size: {
        h: 14,
        w: 21,
        uom: "cm"
    }
    })
    ```