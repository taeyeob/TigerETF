## 목차
1. Tiger ETF 종가 크롤링하기
2. Tiger ETF의 기준가격, 기초지수, 기초지수대비 데이터 불러오기
3. 주의할 점

## Tiger ETF 종가 크롤링하기
1. VSCode를 통해 지난 매크로데이터 크롤링 단계에서 만들었던 폴더에 **tigerprice.py**라는 파일을 생성한다.
2. 같은 폴더에 **tigerprice.csv** 파일을 생성한다.
3. **tigerprice.py** 파일에 다음 코드를 작성한다.

```Python
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
import time
import csv
import pandas as pd

#TIGER 200 IT
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/139260/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows1 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows1.append(output_row)

with open('tigerprice.csv', 'w') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 IT')
    writer.writerows(output_rows1)

#TIGER 200 금융
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/139270/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows2 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows2.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 Finance')
    writer.writerows(output_rows2)

#TIGER 200 건설
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/139220/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows3 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows3.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 construction')
    writer.writerows(output_rows3)

#TIGER 200 산업재
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/227550/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows4 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows4.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 industrial goods')
    writer.writerows(output_rows4)

#TIGER 200 중공업
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/139230/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows5 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows5.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 heavy industry')
    writer.writerows(output_rows5)

#TIGER 200 철강소재
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/139240/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows6 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows6.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 steel')
    writer.writerows(output_rows6)

#TIGER 200 헬스케어
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/227540/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows7 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows7.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 health care')
    writer.writerows(output_rows7)

#TIGER 200 에너지화학
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/139250/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows8 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows8.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 energy chemical')
    writer.writerows(output_rows8)

#TIGER 200 경기소비재
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/139290/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows9 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows9.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 economic consumer goods')
    writer.writerows(output_rows9)

#TIGER 200 생활소비재
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/227560/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows10 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows10.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 consumer goods')
    writer.writerows(output_rows10)

#TIGER 200 커뮤니케이션서비스
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/315270/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows11 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows11.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER communication service')
    writer.writerows(output_rows11)

#TIGER 코스닥150
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/232080/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows12 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows12.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER COSDAQ150')
    writer.writerows(output_rows12)

#TIGER 인버스
path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://m.stock.naver.com/item/main.nhn#/stocks/123310/price")

table = driver.find_element_by_xpath('//*[@id="content_body"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows13 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows13.append(output_row)

with open('tigerprice.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER inverse')
    writer.writerows(output_rows13)
```

4. CMD를 통해 파일을 실행하여 크롤링 데이터를 얻는다.

## Tiger ETF의 기준가격, 기초지수, 기초지수대비 데이터 불러오기
1. **tigerbp.py** 파일을 생성한다.
2. **tigerbp.csv** 파일을 생성한다.
3. **tigerbp.py** 파일에 다음 코드를 입력한다.
```Python
#-*-coding: utf-8-*-
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
import time
import csv
import pandas as pd




path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7139260004")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')[0:59]


output_rows1 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows1.append(output_row)

with open('tigeroutput.csv', 'w') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 IT')
    writer.writerows(output_rows1)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7139270003")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows2 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows2.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 금융')
    writer.writerows(output_rows2)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7139220008")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows3 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows3.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 건설')
    writer.writerows(output_rows3)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7227550001")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows4 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows4.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 산업재')
    writer.writerows(output_rows4)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7139230007")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows5 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows5.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 중공업')
    writer.writerows(output_rows5)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7139240006")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows6 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows6.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 철강소재')
    writer.writerows(output_rows6)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7227540002")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows7 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows7.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 헬스케어')
    writer.writerows(output_rows7)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7139250005")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows8 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows8.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 에너지화학')
    writer.writerows(output_rows8)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7139290001")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows9 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows9.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 경기소비재')
    writer.writerows(output_rows9)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7227560000")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows10 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows10.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 생활소비재')
    writer.writerows(output_rows10)

path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7315270009")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows11 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows11.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 200 커뮤니케이션서비스')
    writer.writerows(output_rows11)

path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7232080002")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows12 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows12.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 코스닥150')
    writer.writerows(output_rows12)



path = '/Users/TaeyeobKim/Desktop/EPIAdvisor/MacroDatas/chromedriver'
driver = webdriver.Chrome(path)
driver.implicitly_wait(3)
driver.get("https://www.tigeretf.com/npc/product/product.do?ksdFund=KR7123310005")

table = driver.find_element_by_xpath('//*[@id="profitDetail"]/table')
rows = table.find_elements_by_tag_name('tr')

output_rows13 = []
for row in rows:
    columns = row.find_elements_by_tag_name('td')
    output_row = []
    for column in columns:
        output_row.append(column.text)
    output_rows13.append(output_row)

with open('tigeroutput.csv', 'a') as csvfile:
    writer = csv.writer(csvfile)
    writer.writerow('TIGER 인버스')
    writer.writerows(output_rows13)

```

## 주의할 점
1. 데이터의 양이 많아 간혹 출력되지 않고 지나가는 ETF들이 보일 수 있는데, 당황하지 않고 출력된 부분을 주석처리한 후 다시 실행하면 된다.
2. 주석처리하는 법: 각 줄마다 앞에 #을 적거나 여러 줄에 블록을 씌운 후 'ctrl + /'을 누르면 주석처리가 된다.
3. 누락된 데이터를 다시 받아오려는 경우, 맨 위에 있는 **with open('tigerprice.csv', 'a') as csvfile:** 부분의 **'a'**를 **'w'**로 바꿔주고 나머지는 놔둬야 한다. 'w'는 write, 'a'는 append의 의미이며, 'w'로 먼저 작성한 후 'a'로 더 써내려간다는 의미의 커맨드이다.