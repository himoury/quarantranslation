import requests
import json
listSurah = json.loads(requests.get("https://unpkg.com/quran-json@1.0.1/json/surahs.json").text)
s = open("bermansur.txt", "r",encoding='utf-8-sig')
sR=s.read().splitlines()
data=[]
j=0
for i in range(len(sR)):

    sR[i]=sR[i].replace("\"","\\\"")
    data.append(sR[i].split("|",2))
    if i==0:
        Aya="{\"number\":\""+data[i][0]+"\",\"name\":\""+listSurah[j]["name"]+"\",\"verses\":[{\"number\":"+data[i][1]+",\"translation\":\""+data[i][2]+"\"}"
        j+=1
    elif data[i][0]==data[i-1][0]:
        Aya=Aya+",{\"number\":"+data[i][1]+",\"translation\":\""+data[i][2]+"\"}"
        if i==len(sR)-1:
            Aya=Aya+"]}"
            fileN=data[i][0]
            o =open(fileN+".json", "a",encoding='utf-8-sig')
            o.write(Aya)
    else :
        Aya=Aya+"]}"
        fileN=data[i-1][0]
        o =open(fileN+".json", "a",encoding='utf-8-sig')
        o.write(Aya)
        Aya="{\"number\":\""+data[i][0]+"\",\"name\":\""+listSurah[j]["name"]+"\",\"verses\":[{\"mumber\":"+data[i][1]+",\"translation\":\""+data[i][2]+"\"}"
        j+=1
