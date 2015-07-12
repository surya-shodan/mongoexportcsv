Mongoexportcsv is a tool to convert MongoDB documents to csv.

It works irrespective of structural differences between individual 
documents. 

eg: 

    If Document A is
	'emp_name': {
		'first_name': 'Jochen',
		'last_name' : 'Rindt'
	}
	
    And Document B is
    	'emp_name': {
		'Full_name': 'Ayrton Senna'
	}


The output csv will be:

		||emp_name||first_name, ||emp_name||last_name, ||emp_name||Full_name
	Doc A   Jochen		      , Rindt                ,
	Doc B                         ,                      , Ayrton Senna

As we can see, the headers contain all possible variable names with 
their hierarchy.
The string sequence '||' is used to signify the hierarchy of the
key in the dictionary.

Pre-requisites:
	Unicodecsv : It's just more versatile to use in place of csv.

To run mongoexport csv : 
	1) Clone the git repository
	2) python mongoexportcsv.py <db_name> <collection_name> <path_to_output_file_name>

Notes:

As you can see, this is clearly barebones and I've just finished coding it.
I'll adding features like using baseCommands to specify command-line args
and so on.
Hope you guys find this useful.

