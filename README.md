
LogCover is An Exception Testing Measurement Tool Based on Exception Log Coverage Analysis.

**Background:**
Exception testing is a crucial part of software testing, and the thoroughness of exception testing directly affects the quality of testing and the stability of the product online. Logcover is a lightweight tool specifically designed to measure the coverage of exception testing by measuring the test coverage of exception logs, as the program branches that print exception logs often require more testing coverage for the exception branches.

**Principle:**
By combining the program source code and the logs generated by test execution, the test coverage of the program's exception logs is calculated. For example: If there are 100 points of exception log (warning, fatal, error) printing in the source code, and during the testing process, 100 logs are generated, corresponding to 50 log printing points in the source code, then the coverage rate of the exception log is 50%. At the same time, logcover will provide all information of the covered and uncovered logs, including file names, line numbers, etc., which facilitates the rapid identification of uncovered exception logs.

**Implementation:**
- Conduct a lightweight static analysis of the source code based on SVN to obtain the original information of exception log printing in the code.
- Collect logs from single-machine/multi-machine testing, and perform parsing, filtering, and merging on the log files to obtain the actual covered log information.
- Calculate the difference based on the original log information in the code and the log information actually generated by the test to determine the coverage rate of the exception log and the coverage information.
- Push the coverage report via email.

**Logcover Usage Instructions:**
1: Download logcover.
2: Modify the corresponding logcover.cfg file. logcover_type =0 indicates single-machine mode; logcover_type =1 indicates multi-machine mode. When choosing multi-machine mode, fill in the machines, user, password, log_paths, and script_path accordingly.
3: Execute sh logcover.sh $svn $log_cover_log_dir $mail_list -s $mail_subject. $svn: The SVN source code path of the program to be tested. $log_cover_log_dir: The path where the log files are stored. $mail_list: The email list for pushing the coverage report, multiple emails are separated by spaces. For example: zhangsan@xx.com li@xx.com. -s $mail_subject: Custom subject for the push email.

**Logcover Execution Environment Dependencies:**
1: Perl v5.8.5+
2: Python v2.7+
3: SVN client v1.6.5+
