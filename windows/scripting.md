```cmd
rem get all env vars
set

rem %variable_name% to get variable_name from env
rem %%f is equivalent to %f, % is used to represent cmd line params, %1, %2, etc.

if exist "%ProgramFiles%\some_dir\some_file" (
    rem do something
) else (
    rem do something else
)

rem use & or && to seperate multiple commands in same line. && -> execute second command only when first command succedes
rem echo. represents line break

cd /d <target_directory_to_cd_to>
cscript <path_to_batch_file_to_run_in_cmd_environment>

rem office 365 managing script ospp.vbs
rem FOR %%parameter IN (set) DO command 
rem FOR /f %%line in ('dir /b some\path\to\some\thing') DO command
```
