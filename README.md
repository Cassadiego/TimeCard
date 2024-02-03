# TimeCard
ejercicio / timeCard

import pandas as pd
import openpyxl
import os

A = (1,2,3,4,5)
B = ['a','b','c','d','f']

data = { 'a': ['julian','ruiz','aprende','python'],
       'b': ['a','b','c','d'],
       'c': ['1','2','3','4'],
       'd': [1.2,3.4,5.6,2.3]
      }

      df1 = pd.DataFrame(data)

df1

df.dtypes

List =[
    ['julian','ruiz','aprende','python'],
    ['a','b','c','d'],
    ['1','2','3','4'],
    [1.2,3.4,5.6,2.3]
    ]

list_columna = ['a','b','c','d']

df2= pd.DataFrame(List, columns=list_columna)

df2

df1

df1.dtypes,df2.dtypes

basepath = 'C:/Users/Casadiego/Documents/ruiz/'

files = os.listdir(basepath)

files

from openpyxl import load_workbook

book='Part 1-REPORTING ANALYST ASSESSMENT.xlsx'

path = basepath+book

list_book = load_workbook(path)

name_sheets = list_book.sheetnames

name_sheets

print(name_sheets)

# Carga los datos desde una sheet específica del Excel
data = pd.read_excel(path, sheet_name= 'Time Card', engine='openpyxl')

data.head(10)

data

data['Duration'] = 'nan'

from datetime import datetime

# Asegurarse de que 'fechaFinalIncapacidad' es de tipo datetime
data['Login Date'] = pd.to_datetime(data['Login Date'])
data['Logout Date'] = pd.to_datetime(data['Logout Date'])

data.shape#forma
data.dtypes

data['Duration']=data['Logout Date']-data['Login Date']
data['Duration']=data['Duration'].dt.total_seconds()
data
