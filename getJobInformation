from selenium import webdriver
import requests
import random
from bs4 import BeautifulSoup
import urllib.request
import time
from selenium.webdriver.common.desired_capabilities import DesiredCapabilities
from lxml.html import fromstring
import pandas as pd
import csv
from parsel import Selector



writer = csv.writer(open('D:\\Soong\\Soong\\businessDataMining\\test.csv', 'w', newline=''))
writer.writerow(['title','Company','Location','Date', 'PeopleNumCurrent','content'])
driver = webdriver.Chrome()
driver.get('https://www.linkedin.com')

accountName='lalala'  #need to change
passward='word'

#input account information
username = driver.find_element_by_class_name('login-email')
username.send_keys(accountName)
time.sleep(2)
password = driver.find_element_by_class_name('login-password')
password.send_keys(passward)
time.sleep(2)
log_in_button = driver.find_element_by_id('login-submit')
time.sleep(2)
log_in_button.click()
time.sleep(2)


# input the recruitment information
def searchRecru(recruInf):
    RelatUrl = []
    for num in range(1000):

        driver.get(
            'https://www.linkedin.com/search/results/all/?keywords=' + recruInf + '%20&origin=GLOBAL_SEARCH_HEADER&page=' + str(
                num))
        time.sleep(4)
        for link in driver.find_elements_by_xpath('//*[@class="ember-view"]'):
            # for link in driver.find_elements_by_css_selector('div > div.search-result__info' ):
            # ember52 > div > div.search-result__info
            a = 0
            try:
                AllUrl = link.get_attribute('href')
            except:
                a = 1
            if (AllUrl and a != 1):
                RelatUrl.append(AllUrl)
            elif a == 1:
                return RelatUrl

jobs=pd.read_csv('D:/Soong/Soong/businessDataMining/jobTitle.csv')

jobs['Sourcing']
jobs['IT supply chain optimization']
jobs['Supply chain']
jobs['Logistics']
jobs['Planning']
jobs['Unnamed: 0']
## get the relative url (all job's)
SourcingUrlALL = []
ITUrlALL = []
SupplyUrlALL = []
LogisUrlALL = []
PlanUrlALL = []
UnnUrlALL = []
for sourc in jobs['Sourcing']:
    urlSourcing = ''
    if spurc is not NaN:
        urlSourcing = searchRecru(spurc)
        SourcingUrlALL.append(urlSourcing)

for IT in jobs['IT supply chain optimization']:
    urlIT = ''
    if IT is not NaN:
        urlIT = searchRecru(IT)
        ITUrlALL.append(urlIT)
for supply in jobs['Supply chain']:
    urlsupply = ''
    if supply is not NaN:
        urlsupply = searchRecru(supply)
        SupplyUrlALL.append(urlsupply)
for Log in jobs['Logistics']:
    urlLog = ''
    if Log is not NaN:
        urlLog = searchRecru(Log)
        LogisUrlALL.append(urlLog)
for plan in jobs['Planning']:
    urlplan = ''
    if plan is not NaN:
        urlplan = searchRecru(Lplanog)
        PlanUrlALL.append(urlplan)
for Unn in jobs['Unnamed: 0']:
    urlUnn = ''
    if Unn is not NaN:
        urlUnn = searchRecru(Unn)
        UnnUrlALL.append(urlUnn)


##get relative information
def getDetails(url):
    driver.get(url)
    morePage = driver.find_element_by_class_name('cta-wrap')  # click the mune('more')
    morePage.click()
    sel = Selector(text=driver.page_source)
    title = sel.xpath('//*[@id="ember1606"]/div[2]/div[1]/h1').extract_first()
    title = str(name).replace('<h1 class="jobs-top-card__job-title t-24">', '').replace('</h1>', '')
    #     title
    Company = sel.xpath('//*[@id="ember1609"]').extract_first()
    Company = Company[136:]
    Company = str(Company).replace('\n</a>', '')

    Location = sel.xpath('//*[@id="ember1606"]/div[2]/div[1]/h3/span[3]').extract_first()
    Location = Location[49:]
    Location = str(Location).replace('</span>', '').replace(' ', '')

    Date = sel.xpath('//*[@id="ember1606"]/div[2]/div[1]/p/span[2]').extract_first()
    Date = str(Date).replace('<span>发布日期:', '').replace('</span>', '')

    PeopleNumCurrent = sel.xpath('//*[@id="ember1606"]/div[2]/div[1]/p/span[3]/span[2]').extract_first()
    PeopleNumCurrent = PeopleNumCurrent.replace('<span>\n', '').replace('</span>', '').replace(' ', '')

    # ALL is means content
    ALL = sel.xpath('//*[@id="ember1610"]/article/div')
    ALL = str(aboutUs).replace(
        '<div class="jobs-description__content jobs-description__content--condensed  jobs-description-content">\n',
        '').replace(
        '<div class="jobs-box__html-content jobs-description-content__text t-14 t-black--light t-normal" id="job-details" tabindex="-1">\n<!----><!---->',
        '').replace('<span>', '').replace('<strong><u>', '').replace('<br>', '').replace('</u>', '').replace(
        '</strong>', '').replace('</u>', '').replace('', '').replace('<li>', '').replace('</li>', '')
    ALL = aboutUs.replace('<strong>', '').replace('</ul>', '').replace('<ul>', '').replace('<!---->', '').replace(
        '</p>', '').replace('</div>', '')
    ALL = aboutUs.replace('</span>', '').replace('<div class="jobs-description__details">', '').replace(
        '<div class="jobs-box__group">', '').replace('<h3 class="jobs-box__sub-title js-formatted-industries-title">',
                                                     '').replace(
        '<li class="jobs-box__list-item jobs-description-details__list-item">', '').replace(
        '<ul class="jobs-box__list jobs-description-details__list js-formatted-job-functions-list">', '').replace(
        '</h3>', '').replace(' <h3 class="jobs-box__sub-title js-formatted-employment-status-title">', '').replace(
        '<div class="jobs-box__group">      <h3 class="jobs-box__sub-title js-formatted-industries-title">', '')
    ALL = ALL.split()

    return title, Company, Location, Date, PeopleNumCurrent, ALL


for url in SourcingUrlALL:
    allTitle=[]
    allCompany=[]
    allLocation=[]
    allDate=[]
    allPeopleNumCurrent=[]
    allContain=[]
    title,Company,Location,Date,PeopleNumCurrent,Contain=getDetails(url)
    allTitle.append(title)
    allCompany.append(Company)
    allLocation.append(Location)
    allDate.append(Date)
    allPeopleNumCurrent.append(PeopleNumCurrent)
    allContain.append(Contain)
    writer.writerow([allTitle,allCompany,allLocation,allDate, allPeopleNumCurrent,allContain])
for url in ITUrlALL:
    allTitle=[]
    allCompany=[]
    allLocation=[]
    allDate=[]
    allPeopleNumCurrent=[]
    allContain=[]
    title,Company,Location,Date,PeopleNumCurrent,Contain=getDetails(url)
    allTitle.append(title)
    allCompany.append(Company)
    allLocation.append(Location)
    allDate.append(Date)
    allPeopleNumCurrent.append(PeopleNumCurrent)
    allContain.append(Contain)
    writer.writerow([allTitle,allCompany,allLocation,allDate, allPeopleNumCurrent,allContain])
for url in SupplyUrlALL:
    allTitle=[]
    allCompany=[]
    allLocation=[]
    allDate=[]
    allPeopleNumCurrent=[]
    allContain=[]
    title,Company,Location,Date,PeopleNumCurrent,Contain=getDetails(url)
    allTitle.append(title)
    allCompany.append(Company)
    allLocation.append(Location)
    allDate.append(Date)
    allPeopleNumCurrent.append(PeopleNumCurrent)
    allContain.append(Contain)
    writer.writerow([allTitle,allCompany,allLocation,allDate, allPeopleNumCurrent,allContain])
for url in LogisUrlALL:
    allTitle=[]
    allCompany=[]
    allLocation=[]
    allDate=[]
    allPeopleNumCurrent=[]
    allContain=[]
    title,Company,Location,Date,PeopleNumCurrent,Contain=getDetails(url)
    allTitle.append(title)
    allCompany.append(Company)
    allLocation.append(Location)
    allDate.append(Date)
    allPeopleNumCurrent.append(PeopleNumCurrent)
    allContain.append(Contain)
    writer.writerow([allTitle,allCompany,allLocation,allDate, allPeopleNumCurrent,allContain])
for url in PlanUrlALL:
    allTitle=[]
    allCompany=[]
    allLocation=[]
    allDate=[]
    allPeopleNumCurrent=[]
    allContain=[]
    title,Company,Location,Date,PeopleNumCurrent,Contain=getDetails(url)
    allTitle.append(title)
    allCompany.append(Company)
    allLocation.append(Location)
    allDate.append(Date)
    allPeopleNumCurrent.append(PeopleNumCurrent)
    allContain.append(Contain)
    writer.writerow([allTitle,allCompany,allLocation,allDate, allPeopleNumCurrent,allContain])
for url in UnnUrlALL:
    allTitle=[]
    allCompany=[]
    allLocation=[]
    allDate=[]
    allPeopleNumCurrent=[]
    allContain=[]
    title,Company,Location,Date,PeopleNumCurrent,Contain=getDetails(url)
    allTitle.append(title)
    allCompany.append(Company)
    allLocation.append(Location)
    allDate.append(Date)
    allPeopleNumCurrent.append(PeopleNumCurrent)
    allContain.append(Contain)
    writer.writerow([allTitle,allCompany,allLocation,allDate, allPeopleNumCurrent,allContain])


