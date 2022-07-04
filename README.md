# FIR_Number
# Finding the consistency of FIR numbers
import pandas as pd
df=pd.read_csv('/file.csv')
df.dropna(inplace = True)
dfnew=df['fir_number'].str.split('/')
f = pd.read_csv('/output.csv')
f["fir_number"]=df['fir_number'] 
print(f)
for i in range(len(dfnew)):
	p=1
	if len(dfnew[i])== 2:
		for j in range(len(dfnew[i])):
			if len(dfnew[i][j])<=4:
				u = int(dfnew[i][j].isnumeric())
				p = p*u
			else:
				p = 0
	else:
		p=0
	f["Correctness"][i] = p
	print('Entry number',i,'Value',p,f["Correctness"][i])
  print(f)
