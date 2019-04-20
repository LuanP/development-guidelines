## Database guidelines !heading

* Database name, tables and columns using snake_case (replace spaces with underscores, e.g.: product_id)
* Take into consideration the [CAP Theorem](http://abiasforaction.net/cap-theorem/) (Consistency, Availability and Partition Tolerance) when choosing the database, always keep in mind that in system distributed through network there's failure in the delivery of messages and therefore in case of losing or delay of messages, it'll be mandatory to choose between consistency or data availabily ([Wikipedia](https://en.wikipedia.org/wiki/CAP_theorem)