import os
import shutil
import pathlib
from queue import Queue

'''
this is python script to change file extension from old_extension to new_extension
useful when downloading files from internet and it has strange extension 

Note: this is only change the extension from file path and doesn't do anything to change the file 
 nature such as format factory program does
    :arguments:
        r: str of the file root directory
        old_extension: str, the old file extension 
        new_extension: str, the desired file extension 
'''
# r: is the string path of the root dir
r = "D:\\guru-remains"
# root: is the path object to the root dir
root = pathlib.Path(r)
# dirs: is a queue incase the dir contains other dirs
dirs = Queue()
dirs.put(root)


# this function changes the extension from the old one to the new
def change_extension(file_path, new_extension='mp4', old_extension='VIDEO_AUDIO'):
    path_str = str(file_path)
    new_path_str = path_str.replace(old_extension, new_extension)
    new_path = pathlib.Path(new_path_str)
    shutil.move(file_path, new_path)


# implementing the logic
while not dirs.empty():
    dir = dirs.get()
    dir_path = pathlib.Path(root, dir)
    for item in os.listdir(dir_path):
        item_path = pathlib.Path(dir_path, item)
        if os.path.isdir(item_path):
            dirs.put(item_path)
        else:
            change_extension(item_path)
