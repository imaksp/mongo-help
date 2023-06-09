## Mongo import/export commands

### INSTALLATION

Follow [this](https://www.mongodb.com/docs/database-tools/installation/installation/) link for installation steps.

### EXPORT COLLECTION (JSON with preserve BSON types)

```bash
mongoexport --uri="mongodb://127.0.0.1:27017/dbName" --jsonFormat=canonical  --collection=textcontent  --out=textcontent.json
```

### EXPORT COLLECTION (CSV with specific fields)

```bash
mongoexport --uri="mongodb://127.0.0.1:27017/dbName" --collection=textcontent --type=csv --fields=name,address --out=/backups/collection.csv
```

### IMPORT COLLECTION

Here mode can be any one from insert, upsert, merge & delete see [this](https://www.mongodb.com/docs/database-tools/mongoimport/#std-option-mongoimport.--mode) for details

```bash
mongoimport --uri="mongodb://127.0.0.1:27017/dbName" --collection=textcontent --type=json --mode=upsert  --file=./textcontent.json
```

### EXPORT ALL (mongodump)

Here remove db name from URI to export all databases.

```bash
mongodump --uri="mongodb://127.0.0.1:27017/dbName" --out=./2023-06-09
```

### IMPORT ALL (mongorestore)

Here `--dir` specifies dump dir location for restore & command will automatically pick database name from dump dir.

```bash
mongorestore --uri="mongodb://127.0.0.1:27017" --dir=./2023-06-09
```
