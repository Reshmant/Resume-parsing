# Resume-parsing
This code extracts the email id,phone no.,address,date of submission from the resume.
#Resume Parsing(Email,Phone no.,Address,Date)
import tika
from tika import parser
import re
class ResumeParsing :
    def parseAnyFile() :
        tika.initVM()
        parsed = parser.from_file('Resume.docx')
        content = parsed["content"]
        print(content+'\n')
        print("After Parsing:")
        emails = re.findall(r'[\w\.-]+@[\w\.-]+', content)
        phnos = re.findall(r'[+0-9 ]{10,15}', content)
        addresses = re.findall(r'Address[\w /,-:]+[.]', content)
        dates = re.findall(r'[0-9]+[,/-]+[0-9]+[,/-]+[0-9]{2,4}', content)
        dollars = re.findall(r'\$[0-9]*[,[0-9]*]*\ ', content)
        print("Email id:")
        for email in emails :
            print('\t', email)
        print("Phone No.:")
        for phno in phnos :
            print('\t', phno)
        print("Addresses:")
        for address in addresses :
            print('\t', address)
        print("Dates:")
        for date in dates :
            print('\t', date)
            
    if __name__ == "__main__" :
        parseAnyFile()
