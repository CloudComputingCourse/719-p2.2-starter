# 719-p2.2-startup
The starter package for 15719 (Spring 2017) Project 2, part 2.
- `download_common_crawl.py` is a simple script that downloads Common Crawl data and stores it in HDFS. It takes in two parameters. The first one is a path file that contains the paths to the WET files to download, one file per line. The second parameter is the number of threads to download files in parallel. We found that 2 threads works the best for one node. It uses `/root/tmp` as scratch space and stores the data in HDFS under `/common_crawl_wet/`. You need to create the two directories before running the script. In the name of downloaded files, backslashes ("/") are replaced with underscores ("_"). For example, when `crawl-data/CC-MAIN-2016-50/segments/1480698540409.8/wet/CC-MAIN-20161202170900-00000-ip-10-31-129-80.ec2.internal.warc.wet.gz` is downloaded, it is stored as `/common_crawl_wet/crawl-data_CC-MAIN-2016-50_segments_1480698540409.8_wet_CC-MAIN-20161202170900-00000-ip-10-31-129-80.ec2.internal.warc.wet.gz` in HDFS.
- `submit` is used to run test for grading and submit your solution. Run it as `./submit <code-path> <test-id> <data-path> <data-file-names> <stop-words-file>`, the arguments are:
  - <code-path> is the local directory that contains your driver program and the `run.sh` script. It should contain nothing else.
  - <test-id> is the single letter (A, B, C, D, or E) that identifies each test case described above. Please make sure the number of slave instances match the test specification or your grading will fail.
  - <data-path> is the path in HDFS under which the WET files for testing are stored.
  - <data-file-names> is the file that contains the names of the WET files to be processed.
  - <stop-words-files> is the path to the stop-words file.
- `get_WARC_dataset.sh` is a script to download Common Crawl data into HDFS. It takes one parameter, which is the number of first WET files to download. This script streamlines the downloading process.
