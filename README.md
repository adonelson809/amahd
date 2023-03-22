# amahd
from data_utils import *
import requests 
import time
import re
from bs4 import BeautifulSoup
from pdb import set_trace
import urllib
import hashlib
import requests
import os
import random
import json
import random
from tqdm import tqdm
from glob import glob
def parse_amazon():
    # good, name, header
    infos = read_json("all_info.json")['item']   
    for info_ith, info in enumerate(infos):
        good = info['good']
        comment_res = []
        next = True
        ith = 0
        max_page_num = 100
        while next and ith <max_page_num:
            print(ith) 
            ith += 1
            url = info['name']
            headers = { n['key']:n['value']  for n in info['request']['header']}
            headers['referer']=headers['referer'].replace("{ith-1}",str(max(1,ith)))
            body = info['request']['body']['raw']
            body = body.replace('{ith}',str(ith))
            res=reque
