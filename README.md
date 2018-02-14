## Mongoexportcsv is a tool to convert MongoDB documents to csv.

### It works irrespective of structural differences between individual documents. 

eg: 

    If Document A is
    {
    	'_id': ObjectId('abcd'),
    	
		'emp_name': {
			'first_name': 'Jochen',
			'last_name' : 'Rindt'
		}
    }
    
    And Document B is
    {	
    	'_id': ObjectId('wxyz'),
    	
	 	'emp_name': {
		'Full_name': 'Ayrton Senna'
		}
    }


The output csv will be:

		||emp_name||first_name, ||emp_name||last_name, ||emp_name||Full_name, '_id
	Doc A	Jochen		      , Rindt                ,                      ,  ObjectId('abcd')
	Doc B   	              ,                      ,  Ayrton Senna        ,  ObjectId('wxyz')

As we can see, the headers contain all possible variable names with 
their hierarchy. If the document does not contain that variable with the
exact hierarchy, it is left empty.
The string sequence '||' is used to signify the hierarchy of the
key in the dictionary.

### Pre-requisites:

	1) Unicodecsv (Just more versatile than csv I guess)
	2) pymongo

### To run mongoexportcsv : 

	1) Clone the git repository
	2) python mongoexportcsv.py <db_name_or_mongodb_uri> <collection_name> <path_to_output_file_name>

### Notes:

The first of the arguments can the name of your database or a complete mongoDb URI: `mongodb://username:password@host:port/databaseName`

As you can see, this is clearly barebones and I've just finished coding it.
I'll be adding features like using baseCommands to specify command-line args
and so on.
Hope you guys find this useful.
