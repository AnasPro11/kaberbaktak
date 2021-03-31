import os,sys

os.system('pip install requests')

os.system('pip install bs4')

os.system('clear')

import requests, json, random, string, time

from bs4 import BeautifulSoup

import os, sys,datetime,time

n = """\x1b[0;32mWelcome To Script Retrieving Megabytes

\033[1;34mTelegram: http://t.me/crazy_net

"""

for c in n:

    sys.stdout.write(c)

    sys.stdout.flush()

    time.sleep(0.03)

else:

    print('\x1b[0;32m')

    log = """

    

░█████╗░███╗░░██╗░█████╗░░██████╗  

██╔══██╗████╗░██║██╔══██╗██╔════╝  

███████║██╔██╗██║███████║╚█████╗░  

██╔══██║██║╚████║██╔══██║░╚═══██╗  

██║░░██║██║░╚███║██║░░██║██████╔╝  

╚═╝░░╚═╝╚═╝░░╚══╝╚═╝░░╚═╝╚═════╝░  

██████╗░██████╗░░█████╗░

██╔══██╗██╔══██╗██╔══██╗

██████╔╝██████╔╝██║░░██║

██╔═══╝░██╔══██╗██║░░██║

██║░░░░░██║░░██║╚█████╔╝

╚═╝░░░░░╚═╝░░╚═╝░╚════╝░

"""

    for c in log:

        sys.stdout.write(c)

        sys.stdout.flush()

        time.sleep(0.0009)

    else:

        x = """

\033[1;34m########## By/Anas pro ##########

\033[1;34m##### script Retrieving Megabytes #####

"""

        

        for w in x:

            sys.stdout.write(w)

            sys.stdout.flush()

            time.sleep(0.05)

        

        else:

                    

                    print("")

                    number = input('\x1b[0;32mEnter Your Number :\x1b[0;39m ').strip()

                    

                    pwd = input("\x1b[0;32mEnter Your Password :\x1b[0;39m ").strip()

                    with requests.Session() as (req):

                        def generationLink(stringLingth):

                            latters = string.ascii_lowercase                            

                            return ''.join((random.choice(latters) for i in range(stringLingth)))

                        url = f"https://web.vodafone.com.eg/auth/realms/vf-realm/protocol/openid-connect/auth?client_id=website&redirect_uri=https%3A%2F%2Fweb.vodafone.com.eg%2Far%2FKClogin&state=286d1217-db14-4846-86c1-9539beea01ed&response_mode=query&response_type=code&scope=openid&nonce={generationLink(10)}&kc_locale=en"

                        responsePageLogin = req.get(url)

                        soup = BeautifulSoup(responsePageLogin.content, 'html.parser')

                        getUrlAction = soup.find('form').get('action')

                        headerRequest = {'Accept':'text/html,application/xhtml+xml,application/xml;q=0.9,image/webp,image/apng,*/*;q=0.8,application/signed-exchange;v=b3;q=0.9',  'Accept-Encoding':'gzip, deflate, br',

                         'Accept-Language':'en-GB,en;q=0.9,ar;q=0.8,ar-EG;q=0.7,en-US;q=0.6',

                         'Connection':'keep-alive',

                         'Content-Type':'application/x-www-form-urlencoded',

                         'Host':'web.vodafone.com.eg',

                         'Origin':'https://web.vodafone.com.eg',

                         'Referer':url,

                         'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.138 Safari/537.36'}

                        formData = {'username':number,  'password':pwd}

                        sendUserData = req.post(getUrlAction, headers=headerRequest, data=formData)

                        checkRegistry = sendUserData.url

                        _checkRegistry = checkRegistry.find('KClogin')

                        if _checkRegistry != -1:

                            code = checkRegistry

                            _code = code[code.index('code=') + 5:]

                            header = {'Accept':'*/*',  'Accept-Encoding':'gzip, deflate, br',

                             'Accept-Language':'en-GB,en;q=0.9,ar;q=0.8,ar-EG;q=0.7,en-US;q=0.6',

                             'Connection':'keep-alive',

                             'Content-type':'application/x-www-form-urlencoded',

                             'Host':'web.vodafone.com.eg',

                             'Origin':'https://web.vodafone.com.eg',

                             'Referer':'https://web.vodafone.com.eg/ar/KClogin',

                             'User-Agent':'Mozilla/5.0 (Windows NT 10.0; Win64; x64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/81.0.4044.138 Safari/537.36'}

                            formDataAccessToken = {'code':_code,  'grant_type':'authorization_code',

                             'client_id':'website',

                             'redirect_uri':'https://web.vodafone.com.eg/ar/KClogin'}

                            sendDataAccessToken = req.post('https://web.vodafone.com.eg/auth/realms/vf-realm/protocol/openid-connect/token', headers=header, data=formDataAccessToken)

                            access_token = sendDataAccessToken.json()['access_token']

                    headers = {'Host':'web.vodafone.com.eg',

                     'msisdn':number,

                     'Authorization':f"Bearer {access_token}",

                     'Connection':'Keep-Alive',

                     'User-Agent':'Mozilla/5.0 (Linux; Android 8.1.0; DRA-LX2) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/70.0.3538.110 Mobile Safari/537.36',

                     'Content-Type':'application/json',

                     'Accept':'application/json'}

                    url = 'https://web.vodafone.com.eg/services/dxl/pom/productOrder'

                    data4 = '{"channel":{"name":"MobileApp"},"orderItem":[{"action":"add","product":{"characteristic":[{"name":"ExecutionType","value":"Sync"},{"name":"LangId","value":"en"}],"relatedParty":[{"id":"%s","name":"MSISDN","role":"Subscriber"}],"id":"MI_LFC_Upgrade_PayDiff","@type":"MI"}}],"@type":"MIProfile"}' % number

                    r4 = requests.post(url, headers=headers, data=data4).text

                    if 'Completed' in r4:

                        

                        print("")

                        print("\x1b[0;32mDone Add")

                        print("\x1b[0;39m")

                        

                    else:

                        print('')

                        print("\x1b[0;31mEROR")

                        print("\x1b[0;39m")

                        

