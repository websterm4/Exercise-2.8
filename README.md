Exercise-2.8
============
#filename defined
filename = 'files/data/HadSEEP_monthly_qc.txt'

#open file
fp = open(filename,'r')

#read file lines
raw_data = fp.readlines()

#close the file
fp.close()

#check data is in program
print raw_data[:10]

#issues: 4 unwanted header lines, each line is a string, white space sperate items

#taking the first year of data in a string
line_data = ' 1873 87.1 50.4 52.9 19.9 41.1 63.6 53.2 56.4 62.0 86.0 59.4 15.7 647.7\n'

#split each item to get a line list
year_data = line_data.split()

#visualise the command
print year_data

line_data = ' 1873 87.1 50.4 52.9 19.9 41.1 63.6 53.2 56.4 62.0 86.0 59.4 15.7 647.7\n'
year_data = line_data.split()

#for loop over the first line for example so each element is converted to a float
for column,this_element in enumerate(year_data):
    year_data[column] = float(this_element)

print 'format now',type(year_data[0])
print year_data

#shows the list of elements minus the first 4 lines of header text
required_data = raw_data[4:]




#cleaned up version

# specify filename
filename = 'files/data/HadSEEP_monthly_qc.txt'

# read the data, chop off first 4 lines 
# and store in required_data
fp = open(filename,'r')
raw_data = fp.readlines()
fp.close()
required_data = raw_data[4:]

# set up list to store data in
data = []


# loop over each line
for line_data in required_data:
    # split on white space
    year_data = line_data.split()
    
    # convert data to float
    for column,this_element in enumerate(year_data):
        year_data[column] = float(this_element)
    data.append(year_data)
    
print data[0]
print data[1]


print data[10][0]
print data[10][1:-1]

c20_data = []
for line in data:
    if (line[0] >= 1900) and (line[0] < 2000):
        c20_data.append(line[1:-1])
 
print c20_data[0]
print max(c20_data[0])

month_names = [ "Jan", "Feb", "Mar", "Apr", \
    "May", "Jun", "Jul", "Aug", "Sep", "Oct", "Nov", "Dec" ]
    
print "In South East England"
for row in xrange(0,100,10):
    year = 1900 + row
    max_precip = max(c20_data[row])
    month = c20_data[row].index(max_precip)
    
print "In the year",year,"the rainiest month was",month_names[month],"with",max_precip,"mm"

result = []
for row in xrange(100):
    result.append(max(c20_data[row]))
    
print "In South East England, the maximum value for the years 1900 to 1999 is"
print result
print "The highest rainfall in a month was",max(result),"mm"
print "It occurred in",result.index(max(result))+1900





