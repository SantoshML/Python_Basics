# Python
#Matplotlib

Created on Fri Jul 28 09:26:10 2017

@author: Santosh Kumar
"""

####----------------      Visualization-----------------------------------####
####-------------------------Histogram------------------------------------####
reset
import pandas as pd
import matplotlib.pyplot as plt
import os.path
plt.style.use('ggplot') ## makes grapg for beautiful.....##
os.chdir('F:\Data Science\Data Science_Python\Intermediate python_edx lab\DAT210x-master\Module3\Datasets')
student = pd.read_csv('students.data',sep = ',',header = 0,index_col = 0)
student.head()
student.dtypes
student.describe()
student.columns
student.index
student.shape
G3 = student.G3
student_df = student[['G3','G2','G1']]
G3.plot.hist(alpha = 0.5)
student_df.plot.hist(alpha = 0.9)

###-----------------------Scatter Plot(2D)------------------------------###
plt.style.use('ggplot')
student.columns.tolist()

student.plot.scatter('sex','address')
student.head()
student.plot.scatter('G2','G3',alpha = 0.8)

###-----------------------Scatter Plot(3D)------------------------------###
import pandas as pd
import os.path
import matplotlib
import matplotlib.pyplot as plt
from mpl_toolkits.mplot3d import Axes3D
plt.style.use('ggplot')
fig = plt.figure()
ax = fig.add_subplot(111,projection='3d')
ax.set_xlabel('Final Grade')
ax.set_ylabel('First Grade')
ax.set_zlabel('Daily Alcohol')
student.columns.tolist()
ax.scatter(student.G1,student.G3,student.Dalc,c='r',marker = '.')
plt.show()
