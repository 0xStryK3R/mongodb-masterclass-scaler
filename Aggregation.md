`AGGREGATION` | [Dataset 13](/Datasets/13.txt)

41. `$match` | [Dataset 13](/Datasets/13.txt)
    ```mongodb
    db.collection.aggregate([
    {
        $match: {
        size: "medium"
        }
    }
    ])
    ```

    
42. `$match` with `$lt` and `$gt` | [Dataset 13](/Datasets/13.txt)
    ```mongodb
    db.collection.aggregate([
    {
        $match: {
        price: {
            $gt: 15,
            $lt: 20
        }
        }
    }
    ])
    ```
    
43. `$project` | [Dataset 13](/Datasets/13.txt)
    1. Selecting Fields
        ```mongodb
            db.collection.aggregate([
        {
            $project: {
            name: 1,
            size: 1
            }
        }
        ])
        ```
        
    -  Bonus - MATCH WITH PROJECT
        ```mongodb
        db.collection.aggregate([
        {
            $project: {
            name: 1,
            size: 1
            }
        }
        ])
        ```
        
    2. Suppressing fields, including _id
        ```mongodb
        db.collection.aggregate([
        {
            $project: {
            _id: 0,
            date: 0
            }
        }
        ])
        ```
        
    3. Conditional projections
        ```mongodb
        db.collection.aggregate([
        {
            $project: {
            name: 1,
            size: 1,
            price: 1,
            "quantity": {
                $cond: {
                if: {
                    $eq: [
                    20,
                    "$quantity"
                    ]
                },
                then: "$$REMOVE",
                else: "$quantity"
                }
            }
            }
        }
        ])
        ```
    
44. Example 44 | [Dataset 13](/Datasets/13.txt)
    1. $project with $add
        ```mongodb
        db.collection.aggregate([
        {
            $project: {
            name: 1,
            total: {
                $add: [
                "$price",
                "$quantity"
                ]
            }
            }
        }
        ])
        ```
        
    2. $project with $multiply
        ```mongodb
        db.collection.aggregate([
        {
            $project: {
            name: 1,
            total: {
                $multiply: [
                "$price",
                "$quantity"
                ]
            }
            }
        }
        ])
        ```
        
    3. $project with $divide
        ```mongodb
        db.collection.aggregate([
        {
            $project: {
            name: 1,
            total: {
                $divide: [
                "$price",
                "$quantity"
                ]
            }
            }
        }
        ])
        ```
    
45. Example 45  | [Dataset 13](/Datasets/13.txt)
    1. $project with $concat
        ```mongodb
        db.collection.aggregate([
        {
            $project: {
            nameSize: {
                $concat: [
                "$name",
                "-",
                "$size"
                ]
            }
            }
        }
        ])
        ```
        
    2. Project, add array fields:
        ```mongodb
        db.collection.aggregate([
        {
            $project: {
            name: 1,
            size: 1,
            date: 1,
            myArray: [
                "$price",
                "$quantity"
            ]
            }
        }
        ])
        ```
    
42. Date and time Operations | [Dataset 13](/Datasets/13.txt)
    ```mongodb
    db.collection.aggregate([
    {
        $project: {
        year: {
            $year: "$date"
        },
        month: {
            $month: "$date"
        },
        day: {
            $dayOfMonth: "$date"
        },
        hour: {
            $hour: "$date"
        },
        minutes: {
            $minute: "$date"
        },
        seconds: {
            $second: "$date"
        },
        milliseconds: {
            $millisecond: "$date"
        },
        dayOfYear: {
            $dayOfYear: "$date"
        },
        dayOfWeek: {
            $dayOfWeek: "$date"
        },
        week: {
            $week: "$date"
        }
        }
    }
    ])
    ```
    
42. Sort, Group, Stage | [Dataset 13](/Datasets/13.txt)
    1. `$sort`
        ```mongodb
        db.collection.aggregate([
        {
            $sort: {
            date: -1
            }
        }
        ])
        ```
        
    2. `$group` + `$push` + `$sort` + `dates`
        ```mongodb
        ```