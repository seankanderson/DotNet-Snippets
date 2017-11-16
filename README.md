## CsvFilePrep.cs
This code processes a CSV file to ensure that any quotes appearing between tokens qualified by quotes are removed. In other words, it will remove quotes between quotes  "Sea"n" = "Sean"


Proven to work against things like this:
"Sean","Anderson""
"Sean",""Anderson"
"Sean"","Anderson"
"Se"an","Anderson"
""Sean"",""Anderson""

 
I wrote it to prep files for SSIS which cannot handle poorly formed text files.  It also removes whitespace such as carrige returns, tabs, or newline characters that appear between quotes.  The files I was processing would have random EOL characters.  Sometimes tab and other times NL and/or CR+NL.  The same coompany would send us SOAP responses with NULL characters. Of course, this code can be adapted to handle other problems you might encounter with text files.  As always, be sure to test, test, test.
 

I used a slight variation of this code to process many large files (tens of Gigabytes each) during a hot cutover where I was receiving the files at the last minute.  Performance is not bad. 

