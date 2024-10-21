# Periodic Table Database Project Documentation

## Overview

This project involves working with a PostgreSQL database named `periodic_table` that contains information about chemical elements. The project includes modifying the existing database structure, creating a bash script to query the database, and implementing version control using Git.

## Database Structure

The database consists of three main tables:

1. `elements`
2. `properties`
3. `types`


### Elements Table

Contains basic information about chemical elements.

Columns:

- `atomic_number` (Primary Key)
- `symbol` (Unique, Not Null)
- `name` (Unique, Not Null)


### Properties Table

Stores physical properties of the elements.

Columns:

- `atomic_number` (Foreign Key referencing `elements.atomic_number`)
- `atomic_mass` (Decimal)
- `melting_point_celsius` (Not Null)
- `boiling_point_celsius` (Not Null)
- `type_id` (Foreign Key referencing `types.type_id`, Not Null)


### Types Table

Categorizes elements into different types.

Columns:

- `type_id` (Primary Key, Serial)
- `type` (VARCHAR(30), Not Null)


## Database Modifications

The following modifications were made to the original database:

1. Renamed columns:

1. `weight` to `atomic_mass`
2. `melting_point` to `melting_point_celsius`
3. `boiling_point` to `boiling_point_celsius`



2. Added constraints:

1. NOT NULL constraints on `melting_point_celsius` and `boiling_point_celsius`
2. UNIQUE constraints on `symbol` and `name` in the `elements` table
3. NOT NULL constraints on `symbol` and `name` in the `elements` table



3. Created the `types` table and established a foreign key relationship with the `properties` table
4. Capitalized the first letter of all element symbols
5. Removed trailing zeros from `atomic_mass` values
6. Added elements Fluorine and Neon to the database
7. Removed non-existent element (atomic number 1000) from the database


## Bash Script (element.sh)

A bash script named `element.sh` was created to query the database and display information about elements. The script accepts an argument (atomic number, symbol, or name of an element) and outputs information about the given element.

### Usage

```shellscript
./element.sh [atomic_number|symbol|name]
```

### Output

The script outputs information in the following format:

```plaintext
The element with atomic number [atomic_number] is [name] ([symbol]). It's a [type], with a mass of [atomic_mass] amu. [name] has a melting point of [melting_point_celsius] celsius and a boiling point of [boiling_point_celsius] celsius.
```

If no argument is provided, the script outputs:

```plaintext
Please provide an element as an argument.
```

If the element is not found in the database, the script outputs:

```plaintext
I could not find that element in the database.
```

## Git Repository

The project is version-controlled using Git. The repository should have at least five commits, with commit messages following the convention:

- fix: for bug fixes and minor changes
- feat: for new features
- refactor: for code refactoring
- chore: for maintenance tasks
- test: for adding or modifying tests


## How to Run

1. Connect to the database:

```plaintext
psql --username=freecodecamp --dbname=periodic_table
```


2. Run the bash script:

```plaintext
./element.sh [argument]
```




## Notes

- The database is designed to be used in a Next.js application with a `layout.tsx` file already in place.
- The project follows best practices for database design, including proper use of foreign keys and constraints.
- The bash script is designed to be efficient and user-friendly, providing clear output based on the input provided.


This documentation provides an overview of the Periodic Table Database project, including its structure, modifications made, and how to use the accompanying bash script. For more detailed information about specific components or processes, please refer to the project files and comments within the code.
