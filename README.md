# Python
#Matplotlib

Created on Fri Jul 28 09:26:10 2017

@author: Santosh Kumar
"""

####----------------      Visualization------------------------------####
####-------------------------Histogram-------------------------------####
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

###-----------------------Scatter Plot(2D)------------------------###
plt.style.use('ggplot')
student.columns.tolist()

student.plot.scatter('sex','address')
student.head()
student.plot.scatter('G2','G3',alpha = 0.8)

###-----------------------Scatter Plot(3D)----------------------###
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

##--------------High DimensionalityViz(Paralle_coordinates)------##

from sklearn.datasets import load_iris
from pandas.tools.plotting import parallel_coordinates
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib

matplotlib.style.use('ggplot')
##---Loadind iris data as datasets.base,bunch----------------------##
data = load_iris()
iris = pd.DataFrame(data.data,columns = data.feature_names)
iris.head()
iris.describe()
iris.dtypes
iris.isnull().sum()
iris.isnull().any().any()

##----------------Creating a new variable in iris dataset----------##

iris['target_names'] = [data.target_names[i] for i in data.target]
#for i in data.target:
    #iris['target_names'][i]  = data.target_names[i]
    
plt.figure() 
parallel_coordinates(iris,'target_names')   
plt.show()    


##---------------------Andrew's Curve(Outlier detection)-----------##
from sklearn.datasets import load_iris
import pandas as pd
import matplotlib.pyplot as plt
import matplotlib
from pandas.plotting import andrews_curves
plt.style.use('ggplot')

data = load_iris()
iris = pd.DataFrame(data.data,columns = data.feature_names)
iris['target_names'] = [data.target_names[i] for i in data.target]
plt.figure() 
andrews_curves(iris,'target_names') 
