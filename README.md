# ServiceLine Backend Engineering Test

## Task Description
Write a single command line PHP script named `importer.php` to perform the following actions:

1. Connect a local SQLite database named `serviceline.db`. This database should be stored on disk and not in memory.
2. Create a table named `customer` to store the data in `AAA1-Customers.csv`.
3. Create a table named `location` to store the data in `AAA1-Locations.csv`.
4. Import the data from `AAA1-Customers.csv` into the `customer` table.
5. Import the data from `AAA1-Locations.csv` into the `location` table.
6. On completion, print the number of customers and locations that were created or updated.

## General Notes
- Assume the program will be run multiple times.
- Assume this is a multi-tenant database where multiple users will store their data.
- It can be assumed all users, customers, and locations are based in the United States.
- You're free to include any open source libraries you'd like to make the task easier.
- Please contain the answer to a single file named `importer.php`. You're free to use any architectural style you wish.
- Empty values should be inserted as `null` wherever possible.
- Create indexes on the `customer` and `location` tables where necessary - assume these can get quite large.
- The following command will be used to execute the script:

```bash
php importer.php AAA1-Customers.csv AAA1-Locations.csv
```

- Output an error if either filepath passed in as arguments to the script does not exist.
- Assume any additional files passed into the script will follow the same format.

## Customer Notes
- A unique, single column, primary key is required.
- A `customer` record should be created if it does not already exist based on the "CustomerNumber" column, updated otherwise.
- A valid `customer` record requires either a non-empty "FirstName" or non-empty "LastName" value.
- Invalid email addresses should be nullified.
- Invalid phone numbers should be nullified.
- Valid phone numbers should be formatted as (XXX) YYY-ZZZZ where X, Y, and Z are all digits.
- A phone number must have a real United States area code to be considered valid.
- The column in the `customer` table that stores the "Birthday" data should be a date and only store valid dates.
- Manually deleting a `customer` record should delete all associated `location` records.

## Location Notes
- A unique, single column, primary key is required.
- A `location` record should be created if it does not already exist based on the "LocationNumber" column, updated otherwise.
- Each `location` record must have a relationship to a `customer` record.
- A `customer` record can have more than one `location` records.
- A valid `location` record requires a non-empty "StreetAddress" value.