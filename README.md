# merge-excel-files-w-python



```python
import pandas as pd
import os

# Specify the directory where the files are located
file_directory = "path/to/your/directory"

# Find all Excel files in the directory
file_names = [f for f in os.listdir(file_directory) if f.endswith('.xlsx')]

# Gather all files into a list
all_files = [pd.read_excel(os.path.join(file_directory, f)) for f in file_names]

# Concatenate all files
merged_file = pd.concat(all_files, ignore_index=True)

# Save the merged file
merged_file.to_excel("merged_file.xlsx", index=False)
```


1. We import the pandas library which is a fast, powerful, and flexible open-source data analysis and manipulation tool.
2. We import the os module which allows us to interact with the underlying operating system in various ways, like working with files and directories.
4. We specify the directory where the Excel files are located.
6. We use a list comprehension to find all files in the specified directory that end with the '.xlsx' extension (which means they are Excel files).
8. We use another list comprehension to read each Excel file found in the previous step and gather them into a list.
10. We use the `concat` function from pandas to merge all the dataframes (which were read from the Excel files) into one dataframe. The `ignore_index=True` parameter means that we ignore the index from each individual file and create a new index for the merged dataframe.
12. We save the merged dataframe to a new Excel file named "merged_file.xlsx". The `index=False` parameter means that we do not write row names (indices).
