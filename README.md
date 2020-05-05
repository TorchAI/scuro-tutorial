# scuro-tutorial
Tutorial for Scuro


## Operator
| Arithmetic Operators |              |                                                              |
|----------------------|--------------|--------------------------------------------------------------|
| Scuro Operator       | SQL Operator | Description                                                  |
|                      | +            | Add                                                          |
|                      | -            | Subtract                                                     |
|                      | *            | Multiply                                                     |
|                      | /            | Divide                                                       |
|                      | %            | Modulo                                                       |
| Bitwise Operators    |              |                                                              |
| Scuro Operator       | SQL Operator | Description                                                  |
|                      | &            | Bitwise AND                                                  |
|                      | |            | Bitwise OR                                                   |
|                      | ^            | Bitwise exclusive OR                                         |
| Comparison Operators |              |                                                              |
| Scuro Operator       | SQL Operator | Description                                                  |
| =                    | =            | Equal to                                                     |
| >                    | >            | Greater than                                                 |
| <                    | <            | Less than                                                    |
| >=                   | >=           | Greater than or equal to                                     |
| <=                   | <=           | Less than or equal to                                        |
| <>                   | <>           | Not equal to                                                 |
| Compound Operators   |              |                                                              |
| Scuro Operator       | SQL Operator | Description                                                  |
|                      | #ERROR!      | Add equals                                                   |
|                      | -=           | Subtract equals                                              |
|                      | *=           | Multiply equals                                              |
|                      | /=           | Divide equals                                                |
|                      | %=           | Modulo equals                                                |
|                      | &=           | Bitwise AND equals                                           |
|                      | ^-=          | Bitwise exclusive equals                                     |
|                      | |*=          | Bitwise OR equals                                            |
| Logical Operators    |              |                                                              |
| Scuro Operator       | SQL Operator | Description                                                  |
|                      | ALL          | TRUE if all of the subquery values meet the condition        |
| {AND}                | AND          | TRUE if all the conditions separated by AND is TRUE          |
|                      | ANY          | TRUE if any of the subquery values meet the condition        |
|                      | BETWEEN      | TRUE if the operand is within the range of comparisons       |
|                      | EXISTS       | TRUE if the subquery returns one or more records             |
|                      | IN           | TRUE if the operand is equal to one of a list of expressions |
|                      | LIKE         | TRUE if the operand matches a pattern                        |
|                      | NOT          | Displays a record if the condition(s) is NOT TRUE            |
| {OR}                 | OR           | TRUE if any of the conditions separated by OR is TRUE        |
|                      | SOME         | TRUE if any of the subquery values meet the condition        |



## Example

An example of Scuro json body:


```
{
    "User": {
        "id{}":{
            "==": 82001
        } 
    },
    "Dummy[]": {
        "Moment": {
            "@column": ["id", "date"]
            "{OR}":{
                "id{OR}": {
                    "==": 234,
                    "{AND}":{
                        "IN": [12, 15, 32, 56], 
                        ">": 20,
                    },  
                    "{AND}":{
                        ">": 400,
                        "<>": 410,
                        "!IN": [420, 500],
                    } 
                }
                "date{OR}": {
                    "IN": ["2017-02-01", "2019-05-01"]
                }           
            },
            "{EXISTS}":{
                "Moment": {
                    "likes{}": "<20"
                },
            }
        }
        "Comment": {
            "{OR}":{
                "momentId{}":{
                    "@": "Dummy[]/Moment/id"
                },
                "userId{}":{
                    "@": "User/id"
                }        
            }           
    }
}

```

