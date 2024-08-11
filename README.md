#Note:
#Run option-1 from main menu to import CSV File data into DataFrame.
#please set font size 12(using Configure IDLE option) to fit all columns on the screen.
#keep your shell window maximize
#For Chart view keep plot windows maximize
#Take care of small and capital letters to input columns names as python/pandas is case sensitive.
intro='''  ------------- CAR SALES Analysis ------------

    This project helps the company to analysis the car sales
    data and summerize reports, we can also visualize the data
    according columns like Brand,Price,Body,Mileage,Engine_Type,
    Year,Model and Sales etc. Sales analysis is the art of
    transforming sales data into actionable insights that help
    boost profitability,enhance customer satisfaction, and
    inform data-driven decisions.
    '''

end_msg='''

    Project Made by Simranjeet Kaur and Manmeet Kaur
    Guru Harkrishan Public School, Kalkaji, New Delhi-110019

    Thank You'''

import matplotlib.pyplot as mpl
import pandas as pd
import numpy as np
import time

main_menu='''\n
            --------MAIN MENU-------
     1. Car Sales Data Import To DataFrame or Export To CSV File
     2. Car Sales Analysis/Data Manipulation
     3. Car Sales Data Visualization
     4. Exit'''

plot_menu='''\n\n            -------PLOT MENU--------
     1.  Line Plot(brands Vs price, Sales)
     2.  Bar Plot(brands Vs mileage)
     3.  Bar Plot(brands Vs year )
     4.  Histogram
     5.  Return to Main Menu'''

analysis_menu='''\n     ------------SEARCH/ADDITION/DELETION--------
     1.  Display All Records
     2.  Search Records based on Selected Column
     3.  Search Records based on Car brands
     4.  Search Records based on Row Label/Number(loc[]/iloc[])
     5.  Display maximum price of the brands specific brand
     6.  Display no of body Details
     7.  Top Five Records
     8.  Last Five Records
     9.  Addition of a New Record to DataFrame
    10.  Deletion of Records from DataFrame
    11.  Addition of a New Column to DataFrame
    12.  Display dataframe information
    13.  Display description of DataFrame(aggregate functions)
    14.  Return to Main Menu'''

import_export_menu='''     ------IMPORT/EXPORT MENU------
     1.  Import CSV to DataFrame
     2.  Export DataFrame Data to CSV File
     3.  Return to Main Menu'''


for i in intro:
     print(i,end='')
     time.sleep(0.0001)


while True:
    print(main_menu)
    ch=int(input('Enter your choice -> '))
    if ch==1:
        while True:
            print(import_export_menu)
            ch3=int(input('Enter your choice ->  '))
            if ch3==1:
                df=pd.read_csv(r'C:\Users\Sddc\Desktop\PROJECT WORK\CARS SALES ANALYSIS\car_sales_analysis.csv')
                pd.set_option('display.expand_frame_repr',False) #To display data in expanded form
                pd.set_option('display.max_rows',40)   #To display all rows on screen
                print('Content of data frame ')
                print(df)
                print()
            elif ch3==2:
                df.to_csv("car_sales_analysis.csv", index = False, header=True)
                print('\nData Written in [car_sales_analysis.csv] file.........\n\n')
            elif ch3==3:
                print('\n.........Back to Main menu........\n\n')
                break
            else:
                print('\nWrong Choice\n')
    elif ch==2:
        while True:
            print(analysis_menu)
            ch1=int(input('Enter your choice ->  '))
            if ch1==1:
                print(df)
                print()
            elif ch1==2:
                print('\nList of Columns are [')
                for x in df.columns:
                    print(x,end=', ')
                print(' ]')
                clist=[]
                while True:
                    c=input('\nEnter column name -> ')
                    clist.append(c)
                    ch=input('Want to give more column name-> ')
                    if ch in 'nN':
                        break
                print('Details of Selected columns data')
                print(df[clist])
                print()
            elif ch1==3:
                n=input('Enter Car Brand -> ')
                df1=df[df.brand==n]
                if df1.empty:
                    print('\n.......sorry no data for this group........')
                else:
                    print(df1)
                print()
            
