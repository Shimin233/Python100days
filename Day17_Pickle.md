## The Pickle module
The module of Pickle can store almost everything in the form of binary numbers, permanently(?).

Storing is called 'pickling' and reading 'unpickling'.

```Python
>>> import pickle
>>> my_list = [123, 2.33, 'me', ['another list']]
>>> pickle_file = open('my_list.pklanyext', 'wb') #the extension of the newly created file can be any text: pkl, pklanyext, whateverext, etc; 'wb' means 'writing binary'
>>> pickle.dump(my_list, pickle_file)  #dump the contents into the new file, like making pickle :)
>>> pickle_file.close()
>>> pickle_file = open('my_list.pklanyext', 'rb') #'rb' means 'reading binary'
>>> my_list2 = pickle.load(pickle_file)
>>> print(my_list2)
[123, 2.33, 'me', ['another list']]
```
I can see the file with its path /Users/shiminfu/Documents/my_list.pklanyext.
Pickle can be used to store a large amount of file and read it in one line. Take an exmaple, first create the pickle file 'city_data.pkl'. For convenience I only insert three cities: '北京', '上海', '天津'.
```Python
>>> city = {'北京':'101010100', '上海':'101020100', '天津':'101030100'}
>>> pickle_file = open('city_data.pkl', 'wb')
>>> pickle.dump(city, pickle_file)
>>> pickle_file.close()
#try to read it
>>> list2= pickle.load(open('city_data.pkl', 'rb'))
>>> list2
{'北京': '101010100', '上海': '101020100', '天津': '101030100'}
```
Then create the program and quote the pickle file created above. Remark that to quote some file, the quoted file should be in the same folder as the program does; here I copy `city_data.pkl` to /Users/shiminfu/Desktop/WithoutOneDrive/Studies/Python100days/Day17. Is there a method to create a pickle file in some specified path?(TBC) Type in the module
```Python
import urllib.request
import json
import pickle

pickle_file = open('city_data.pkl', 'rb')
city = pickle.load(pickle_file)

password = input('Please insert a city: ')
name1 = city[password]
File1 = urllib.request.urlopen('http://m.weather.com.cn/data/'+name1+'.html') #open url
weatherHTML = File1.read().decode('utf-8') #read the opened url
weatherJSON = json.JSONDecoder().decode(weatherHTML) #create json
weatherInfo = weatherJSON['weatherinfo']
#print the info
print('City: ', weatherInfo['city'])
print('Weather in 24 hours: ')
print('Temperature: ', weatherInfo['temp1'])
print('Weather: ', weatherInfo['weather1'])

print('Press any key to exit: ')                               
```
Remark, it is recommended to put the program and the pickle file in one folder (e.g. the folder 'Weather') so it is tidy and ensures quotation of pickle.
The program has a smaller size when quoting the city data instead of writing them directly.
PS. the program does not work here because there is a problem with the website, do not mind this and just learn the coding here.

## Keys
- The `pickle` module
  - create and store info in a pickle file
  - quote a pickle file 
