Atitit golan query and bind to map



If need many code ...

var db sql.DBvar sqlcommand string
rows, _ := db.Query(sqlcommand)
cols, _ := rows.Columns()
data := make(map[string]string)if rows.Next() {
    columns := make([]string, len(cols))
    columnPointers := make([]interface{}, len(cols))
    for i, _ := range columns {
        columnPointers[i] = &columns[i]
    }
    rows.Scan(columnPointers...)
    for i, colName := range cols {
        data[colName] = columns[i]
    }
}

