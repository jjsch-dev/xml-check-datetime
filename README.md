XML Date time Utility
====


xml_datetime.py is an open source command line utility in Python to verify the consistency of the IN-2 and API-400x equipment history files obtained with the itk_tool application.

It mainly checks the validity of the date and time and that the sequence is ascending.

If the identifiers were generated in the history, (for example incremental by one), it is possible to detect if there are any out of sequence.

If the identifiers were registered and all the actions in the history were activated, it is possible to detect unaccepted markings.

In addition to the report in the console, it is possible to generate a file in CSV format, (Comma-separated values) with the command --gen_csv, and in turn it is possible to choose the format of the output file with the configuration file csv_format.js

The file has the following structure:
```json
{
    "sep":" ", separator used between fields, in this case a space
    "fields":{ list of fields that make up the file. A field is excluded by removing it
        "index": "{:05}", inserts the index of the register, in this case 10 fixed digits.
        "card_id": "{:08}", inserts the card identifier.
        "date":{  inserts the date and specifies the format. A field is excluded by removing it.
            "sep": "/", date separator.
            "day": "{:02}", first field is the day of the month.
            "month": "{:02}", second field is the month.
            "year": "{:02}", last field is the year.
        },
        "time":{ inserts the date and specifies the format. A field is excluded by removing it.
            "sep": ":", time separator.
            "hour": "{:02}", first field is the hour.
            "minute": "{:02}", second field is the minutes.
            "seconds":"{:02}" last field is the seconds
        },
        "source": "{:02}", mark source (readers, biometric, etc)
        "event_code" : "{:03}", mark status code (1 = ok)
        "error": "string", includes the code resulting from the analysis in string format. (ok, dt_invalid, dt_sequence, id_sequence)
}
```
Notes on formatting the output file
-----------------------------------
1) The order of the field is what it has in the json file.
2) For a field not to be present, it is simply removed from the format file.
3) The number of digits follows the python string format, for example for fixed fields with leading zeros {: 08}, where 8 indicates the size of the field and that it is completed with zeros.
4) The error field has two options, when you use the string tag, the output is: ok, dt_invalid, dt_sequence, id_sequence. And when it is numeric the output is: 1, 2, 3, 4 respectively.


Installation
------------
For Windows, there are two executables in the dist folder, one for x86 and one for amd64.
Note: to generate the output file, it is necessary to copy the csv_format.js file in the same folder as the executable.

Support
-------

If you need assistance, contact me:

* Email      : juanschiavoni@gmail.com


Contributing
------------


Licenses
--------

- xml_datetime.py is released under the terms of the MIT License. Please refer to the
  LICENSE file.


