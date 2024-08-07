
# Retail Transaction Project

# Problem Statement
This is a dataset containing retail transaction from large retailer,with over 100 thousand records spanning 2 years. Each record represents a single transaction and includes features such as:
- Customer ID (Anonymous)
- Product ID
- Quantity 
- Price 
- Transaction Date 
- Discount Applied 
- Payment Method
- Store Location etc.
my goal is to analyze this dataset to determine:

1.  The Total Amount by Day Name
2.  The Total Amount by Month Name
3.  The Total Amount Quarterly 
4.  The Total Amount yearly
5.  The Total Revenue of Each Product 
6.  The Best Payment Method 

# LIBRARY USED
1. Matplotlib
2. Pandas
3. Numpy

# STEPS
- rounding up the total amount column to the nearest decima place. Retail['TotalAmount']=Retail['TotalAmount'].round()
- converting the transaction date column from an object type to date time type. Retail["TransactionDate"]=pd.to_datetime(Retail["TransactionDate"])

1. Total Amount by Day Name 
Retail["Day_Name"]=Retail["TransactionDate"].dt.day_name()
Dayname=Retail.groupby("Day_Name")["TotalAmount"].sum().round()
Dayname

Name=Dayname.index  
Number=Dayname.values

plt.bar(Name,Number)
plt.title("Transaction per day",fontsize=30,fontstyle='italic')  
plt.savefig("transaction per day")  
plt.show()
![transaction per day](https://github.com/user-attachments/assets/bafa6b30-473e-4575-aa38-ac8d33c9d63d)

2. Total Amount by Month Name 
Retail["Month_Name"]=Retail["TransactionDate"].dt.month_name()
Month_Name=Retail.groupby("Month_Name")["TotalAmount"].sum().round()  
Month_Name

Name1=Month_Name.index  
Number1=Month_Name.values

plt.pie(Number1,labels=Name1,autopct="%1.0f%%")
plt.title("Transaction per month",fontsize=30,fontstyle='italic')
plt.savefig("transaction per month")  
plt.show()
![transaction per month](https://github.com/user-attachments/assets/c6845432-9dc0-45b4-aaea-18e10a96713e)

3. Total Amount by Quarterly
Retail["Quarter"]=Retail["TransactionDate"].dt.quarter
quarter=Retail.groupby("Quarter")["TotalAmount"].sum().round()
quarter

Name2=quarter.index  
Number2=quarter.values

plt.plot(Name2,Number2)
plt.title("Transaction per quarter",fontsize=30,fontstyle='italic')  
plt.savefig("transaction per quarter")  
plt.show()
![transaction per quarter](https://github.com/user-attachments/assets/d23a45ce-7f4c-4700-a046-6764cef08d0b)

4. Total Amount Per year
Retail["Year"]=Retail["TransactionDate"].dt.year
year=Retail.groupby("Year")["TotalAmount"].sum().round()  
year  
Name3=year.index  
Number3=year.values

![trans per year](https://github.com/user-attachments/assets/95b0b320-361a-45b9-99d3-57531e9495ac)

5. Total Revenue per Product
Revenue=Retail.groupby("ProductCategory")["TotalAmount"].sum().round()  
Revenue

Name4=Revenue.index  
Number4=Revenue.values 

![revenue](https://github.com/user-attachments/assets/253836b2-587a-4437-8c25-c09f2253a5cd)

6. Best Payment Method
Payment=Retail.groupby("PaymentMethod")["TotalAmount"].sum().round()  
Payment

Name5=Payment.index  
Number5=Payment.values

plt.scatter(Name5,Number5)  
plt.title("best payment methods",fontsize=30,fontstyle='italic')
plt.savefig("payment method")  
plt.show()

![payment method](https://github.com/user-attachments/assets/11cb0637-b9bf-4917-bbdc-cb9620489a19)


# SCREENSHOT OF THE CHART IN SUBPLOT

fig,Retails=plt.subplots(nrows=2,ncols=3,figsize=(14,8))  
fig.suptitle("RETAIL TRANSACTION",fontsize=40, fontstyle="italic", fontweight="bold",c="r")  
Retails[0,0].bar(Name,Number)
Retails[0,1].pie(Number1,labels=Name1,autopct="%1.0f%%")
Retails[0,2].plot(Name2,Number2,marker="o")  
Retails[1,0].barh(Name3,Number3)
Retails[1,1].pie(Number4,labels=Name4,autopct="%1.0f%%",shadow=True,explode=[0,0.1,0.1,0])  
Retails[1,2].scatter(Name5,Number5,marker="*")


Retails[0,0].set(title="Transaction per day")  
Retails[0,1].set(title="Transaction per month")  
Retails[0,2].set(title="Transaction per quarter")  
Retails[1,0].set(title="Transaction per year")  
Retails[1,1].set(title="Revenue per category")  
Retails[1,2].set(title="Best payment method")  

plt.tight_layout()  
plt.savefig("retail trans")  
plt.show()

![retail trans](https://github.com/user-attachments/assets/64b3965e-92b3-41d0-ac63-cf1d6c3cde43)
