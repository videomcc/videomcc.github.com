=================== VideoMCC Dataset ===================
1. Specifications
2. Download instructions
3. Notes
4. Licensing information


================== Specifications ===================
Dataset consists of video and textual data.

Video: 272504 video clips, each one is 2-5 seconds long, total of 1.8TB. Video resolution is 171x128.
Video files naming and directory structure:
Each clip has an 8-digit filename, e.g. 00000001.avi. Every subdirectory of the directory 00/ has exactly 1000 files except for the last subdirectory that contains 504 files.


Captions files: captions.train and captions.test, each contains sentences for training and testing sets, respectively. One sentence per line.


Task files: task.train and task.test for training and testing sets respectively.
- task.train contains one multiple-choice question per line in the following format (separated by space):
v_id s_id1 s_id2 s_id3 s_id4 s_id5 k
v_id is an 8-digit id of a video, which is the same as clip filename.
s_id1, ..., s_id5 are caption indices that correspond to line number in the caption file.
k is a single number from 1-5 denoting the index of a correct answer among five sentences.

- task.test contains one multiple-choice question per line in the following format (separated by space):
v_id s_id1 s_id2 s_id3 s_id4 s_id5
v_id is an 8-digit id of a video, which is the same as clip filename.
s_id1, ..., s_id5 are caption indices that correspond to line number in the caption file.


=============== Download instructions ===============
VideoMCC dataset consists of 274 tar-files: 00000.tar.gz to 00272.tar.gz contain video files, vicom.tar.gz contains captions and task files as described in the previous section.

Currently two options for data downloading are available: using Internet Archive tool or using any other download manager.

1. Download using Internet Archive tool

To download data from archive.org web-site using internetarchive command-line tool:
- install the tool (described in more detail on the tool User's Guide web-page https://internetarchive.readthedocs.io/en/latest/)
	$ curl -LOs https://archive.org/download/ia-pex/ia
	$ chmod +x ia
- get the list of items from http://videomcc.org/files/items.lst
- make sure your Python is of the version 2.9 or newer
- run the command
	$ ia download --verbose -I items.lst --glob=\*.tar.gz --no-directories --destdir=<your-destination-directory>

2. Downloading using other download managers

To download using your favorite download manager get the list of URLs from
http://videomcc.org/files/downloadURLs.lst

MD5 checksums for archive files are available at http://videomcc.org/files/checksum.md5
After downloading unzip archives using tar utility. Please note, that tar-files require 1.2TB in total and video files after unzipping require 1.8TB in total.


======================= Notes =======================
For data processing we successfully used OpenCV 2.4.10 and ffmpeg-3.0.1. Earlier versions of this software may or may not be compatible with AVI codec used for video encoding.


=============== Licensing information ===============
The VideoMCC dataset was created from TV News Shows donated by Internet Archive for research purpose and is subject to Terms of Use available at https://archive.org/about/terms.php.
VideoMCC collection is available for free to research groups, individual researches and non-profit organizations. For commercial use please contact the Archive at info@archive.org.

In case you are using VideoMCC dataset in your research we would kindly appreciate if you cite the paper
@article{DBLP:journals/corr/TranPT16,
  author    = {Du Tran and Maksim Bolonkin and
               Manohar Paluri and
               Lorenzo Torresani},
  title     = {VideoMCC: a New Benchmark for Video Comprehension},
  journal   = {CoRR},
  volume    = {abs/1606.07373},
  year      = {2016},
  url       = {http://arxiv.org/abs/1606.07373}
}
