import datetime
from tabulate import tabulate

dataGudang = [
    {
        'Kode' : 111,
        'Nama' : 'Kursi',
        'Stock' : 10,
        'Tanggal masuk' : '02/05/2023',
        'Tanggal keluar' : '23/05/2023',
    },
    {
        'Kode' : 112,
        'Nama' : 'Meja',
        'Stock' : 10,
        'Tanggal masuk' : '12/05/2023',
        'Tanggal keluar' : '15/05/2023',
    },
    {
        'Kode' : 113,
        'Nama' : 'Kasur',
        'Stock' : 10,
        'Tanggal masuk' : '20/05/2023',
        'Tanggal keluar' : '27/05/2023',        
    }
]

kosong = []

# Function pelengkap
def balikMainMenu () :
    konfirmasi = input('Kembali ke main menu ? (yes/no): ').lower()
    return konfirmasi

def pilihKolom(perintah) :
    cariKolom = input(
        '''
        Kolom data :
        1. Kode barang
        2. Nama barang
        Pilih nomor kolom data yang digunakan untuk {} data: '''.format(str(perintah))
    )
    return cariKolom

def savingData() :
    konfirmasiSimpan = input('\nApakah anda akan menyimpan data tersebut? (yes/no): ').lower()
    return konfirmasiSimpan

def cariDataExist(input,k) :
    
    p = 0

    if k == 'Kode' :
        cari = 'Kode'
    elif k == 'Nama' :
        cari = 'Nama'  

    for i in range(len(dataGudang)) :
        if dataGudang[i][cari] == input :
            index = i
            dataExist = True
            break
        else :
            p += 1
            if p >= (len(dataGudang)) :
                dataExist = False
                print('\n THE DATA YOU ARE ALREADY LOOKING FOR DOES NOT EXIST!')
                index = 0
                break

    return dataExist, index


# Function Reading

def optionReading() : # Menampilkan menu reading
    hasilReading = input('''
    Reading Sub Menu:
    1. Menampilkan keseluruhan data
    2. Menampilkan data tertentu
    3. Kembali
    Silahkan masukan angka yang ingin dijalankan : ''')
    return hasilReading

def seluruhData(list) : # Untuk menampilkan data 
    Kolom = list[0].keys()
    Baris =  [x.values() for x in list]
    print('\n', tabulate(Baris, Kolom))

def cariDataReading(input, k) : 
    p = 0

    if k == 'Kode' :
        cari = 'Kode'
    elif k == 'Nama' :
        cari = 'Nama'
    
    for i in range(len(dataGudang)) :
        if dataGudang[i][cari] == input :
            kosong.append(dataGudang[i])
            seluruhData(kosong)
            kosong.clear()
            break   
        else :
            p += 1
            if p >= (len(dataGudang)) :
                print('\n DATA DOES NOT EXIST!')
                break   
            
def dataTertentu() :  # Untuk mencari data tertentu

    while True :
        hasilKolom = pilihKolom('mencari')

        if hasilKolom == '1' :
            kodeBarang = int(input('Input kode barang yang ingin dicari (masukkan angka): '))
            cariDataReading(kodeBarang, 'Kode') 
            break

        elif hasilKolom == '2' :
            namaBarang = input('Input nama barang yang ingin dicari :').capitalize()
            cariDataReading(namaBarang, 'Nama')
            break

        else :
            print('\n INPUT SALAH!')
            continue       
            
    
# Function Create   
def optionCreate() : # Untuk menampilkan menu create
    hasilCreate = input('''
    Creating Sub Menu:
    1. Menambahkan data
    2. Kembali 
    Silahkan masukan angka yang ingin dijalankan : ''')
    return hasilCreate

def cariDuplikatCreate(input, k) : # Untuk filter data duplikat

    if k == 'Kode' :
        cari = 'Kode'
    elif k == 'Nama' :
        cari = 'Nama'  

    for i in range(len(dataGudang)) :
        if dataGudang[i][cari] == input :
            print('\n DATA ALREADY EXIST!')
            dataDuplikat = True
            break
        else :
            dataDuplikat = False
    return dataDuplikat

def inputTanggal () : # Untuk input tanggal baru
    while True :

        tglMasuk = input('Silahkan input tanggal masuk barang baru (DD/MM/YYYY): ')

        if len(tglMasuk) < len('DD/MM/YYYY') or len(tglMasuk) > len('DD/MM/YYYY') :
            print('Pastikan format tanggal DD/MM/YYYY')
            continue

        tglIn = tglMasuk.split('/')
                   
        tglInInt = [int(i) for i in tglIn]
                    
        if tglInInt[0] > 31 or tglInInt[1] > 12 :
            print('Pastikan tanggal tidak lebih dari 31 atau bulan tidak lebih dari 12')
            continue
        else :
            break

    while True :

        tglKeluar = input('Silahkan input tanggal keluar barang baru (DD/MM/YYYY): ')

        if len(tglKeluar) < len('DD/MM/YYYY') or len(tglKeluar) > len('DD/MM/YYYY') :
            print('Pastikan format tanggal DD/MM/YYYY')
            continue

        tglOut = tglKeluar.split('/')

        tglOutInt = [int(i) for i in tglOut]

        if tglOutInt[0] > 31 or tglOutInt[1] > 12 :
            print('Pastikan tanggal tidak lebih dari 31 atau bulan tidak lebih dari 12')
            continue
        elif tglOutInt[0] < tglInInt[0] or tglOutInt[1] < tglInInt[1] :
            print('Pastikan tanggal atau bulan keluar lebih dari tanggal atau bulan masuk')
            continue
        else :
            break

    return tglMasuk, tglKeluar


def tambahData() : # untuk menambahkan data
    
    while True :
        hasilKolom2 = pilihKolom('menambah')
        
        if hasilKolom2 == '1'  :
            
            kolomKodeTambah = int(input('Silahkan input kode barang baru (angka): '))

            konfirmasiDuplikat = cariDuplikatCreate(kolomKodeTambah, 'Kode')
            
            while konfirmasiDuplikat != True :

                nama = input('Silahkan input nama barang baru : ').capitalize()
                stock = int(input('Silahkan input stock barang baru (angka): '))

                tanggal = inputTanggal()

                tglMasuk = tanggal[0]
                tglKeluar = tanggal[1]

                kosong.append({
                    'Kode' : kolomKodeTambah,
                    'Nama' : nama,
                    'Stock' : stock,
                    'Tanggal masuk' : tglMasuk,
                    'Tanggal keluar' : tglKeluar,
                })

                seluruhData(kosong)
                k = savingData()
                if k == 'yes' :
                    dataGudang.append(kosong[0])
                    print ('\nDATA SUCCESSFULLY SAVED!')
                    kosong.clear()
                    break
                else :
                    kosong.clear()
                    break
            
            break


        elif hasilKolom2 == '2' : 
            kolomNamaTambah = input('Silahkan input nama barang baru: ').capitalize()

            konfirmasiDuplikat = cariDuplikatCreate(kolomNamaTambah, 'Nama')
            
            while konfirmasiDuplikat != True :

                kode = int(input('Silahkan input kode barang baru (angka): '))
                stock = int(input('Silahkan input stock barang baru (angka): '))

                tanggal = inputTanggal()

                tglMasuk = tanggal[0]
                tglKeluar = tanggal[1]
 
                kosong.append({
                    'Kode' : kode,
                    'Nama' : kolomNamaTambah,
                    'Stock' : stock,
                    'Tanggal masuk' : tglMasuk,
                    'Tanggal keluar' : tglKeluar,
                })

                seluruhData(kosong)
                k = savingData()
                if k == 'yes' :
                    dataGudang.append(kosong[0])
                    print ('\nData SUCCESSFULLY SAVED!')
                    kosong.clear()
                    break
                else :
                    kosong.clear()
                    break

            break
            
        else :
            print('\n INPUT SALAH!')
            continue  


# Function Update

def optionUpdate() : # Untuk menampilkan menu update
    hasilUpdate = input('''
    Update Sub Menu:
    1. Memperbaharui data
    2. Kembali 
    Silahkan masukan angka yang ingin dijalankan: ''')
    return hasilUpdate

def konfirmasiUpdateData(konfirmasi, baris) : # Untuk konfirmasi update data yang diperbaharui
    while konfirmasi == True :
        print('\n{}'.format(dataGudang[baris]))
        lanjutUpdate = input('\nApakah anda ingin melanjutkan memperbaharui data? (yes/no): ').lower()

        if lanjutUpdate == 'yes' :
            kolomMana = input('Ketik nama kolom yang datanya ingin diubah: ').capitalize()
                    
            if kolomMana == 'Kode' or kolomMana == 'Stock' :
                dataUpdateInt = int(input('Ketik data baru (angka) : '))
                t = savingData()
                if t == 'yes' :
                    dataGudang[baris][kolomMana] = dataUpdateInt
                    print('\nDATA SUCCESSFULLY UPDATE!\n')
                    break
                else :
                    break

            elif kolomMana == 'Nama' :
                dataUpdateStr = input('Ketik data baru: ').capitalize()
                t = savingData()
                if t == 'yes' :
                    dataGudang[baris][kolomMana] = dataUpdateStr
                    print('\nDATA SUCCESSFULLY UPDATE!')
                else :
                    break

            else :
                dataUpdateStr = input('Ketik data baru: ')
                t = savingData()
                if t == 'yes' :
                    dataGudang[baris][kolomMana] = dataUpdateStr
                    print('\nDATA SUCCESSFULLY UPDATE!')
                else :
                    break
                    
            break

        else :
            break
    
    return True

def updateData() : # Untuk memperbaharui data

    while True :
        hasilKolom3 = pilihKolom('merubah')
        
        if hasilKolom3 == '1'  :
            kolomKodeUbah = int(input('Silahkan input kode barang yang datanya ingin diubah: '))

            hasilCari = cariDataExist(kolomKodeUbah,'Kode')
            kondisi = hasilCari[0]
            index = hasilCari[1]

            a = konfirmasiUpdateData(kondisi, index)
            if a == True :
                break
          
        elif hasilKolom3 == '2' :
            kolomNamaUbah = input('Silahkan input nama barang yang datanya ingin diubah: ').capitalize()

            hasilCari = cariDataExist(kolomNamaUbah,'Nama')
            kondisi = hasilCari[0]
            index = hasilCari[1]

            a = konfirmasiUpdateData(kondisi, index)
            if a == True :
                break

        else :
            print('\n INPUT SALAH!')
            continue  

# Function Delete
def optionDelete() : # Untuk menampikan menu update
    hasilDelete = input('''
    Delete Sub Menu:
    1. Menghapus data
    2. Kembali 
    Silahkan masukan angka yang ingin dijalankan: ''')
    return hasilDelete

def menghapusData(konfirmasi, baris) : # Untuk menghapus data 

    while konfirmasi == True :
        print('\n{}'.format(dataGudang[baris]))
        lanjutDelete = input('\nApakah anda ingin melanjutkan menghapus data? (yes/no): ').lower()

        if lanjutDelete == 'yes' :
            del dataGudang[baris]
            print('\nDATA SUCCESSFULLY DELETED!')
            break
        else :
            break
    
    return True

def deleteData() : # Untuk memilih data yang akan dihapus
    
    while True :
        hasilKolom4 = pilihKolom('menghapus')
       
        if hasilKolom4 == '1'  :
            kolomKodeHapus = int(input('Silahkan input kode barang yang datanya ingin dihapus: '))

            hasilCari = cariDataExist(kolomKodeHapus, 'Kode')       
            kondisi = hasilCari[0]
            index = hasilCari[1]

            a = menghapusData(kondisi, index)
            if a == True :
                break

        elif hasilKolom4 == '2' :
            kolomNamaHapus = input('Silahkan input nama barang yang datanya ingin dihapus: ').capitalize()   

            hasilCari = cariDataExist(kolomNamaHapus, 'Nama')           
            kondisi = hasilCari[0]
            index = hasilCari[1]

            a = menghapusData(kondisi, index)
            if a == True :
                break

        else :
            print('\nINPUT SALAH!')
            continue


#Function Holding Cost

def optionHoldingCost() : # Untuk menampilkan menu holding cost
    hasilHolding = input('''
    Holding Cost Sub Menu:
    1. Menghitung biaya simpan dari tanggal masuk sampai tanggal keluar
    2. Menghitung biaya simpan dari tanggal masuk sampai tanggal hari ini 
    3. Kembali
    Silahkan masukan angka yang ingin dijalankan: ''')
    return hasilHolding


def holdingCost(angka) : # Untuk menghitung holding cost

    while True :
        seluruhData(dataGudang)
        nomor = int(input('\nInput kode barang yang ingin dihitung biaya simpan: '))

        hasilCari = cariDataExist(nomor, 'Kode') 
        kondisi = hasilCari[0] 
        index = hasilCari[1] 
        
        while kondisi == True :
            tanggalMasuk = dataGudang[index]['Tanggal masuk']
            listTanggalMasuk = tanggalMasuk.split('/')
            listTanggalMasukInt = [int(i) for i in listTanggalMasuk]

            tanggalIn = listTanggalMasukInt[0]
            bulanIn = listTanggalMasukInt[1]
            tahunIn = listTanggalMasukInt[2]

            formatIn = datetime.date(tahunIn, bulanIn, tanggalIn)
        
            if  angka == '1':
                tanggalKeluar = dataGudang[index]['Tanggal keluar']
                listTanggalKeluar = tanggalKeluar.split('/')
                listTanggalKeluarInt = [int(i) for i in listTanggalKeluar]
                tanggalOut = listTanggalKeluarInt[0]
                bulanOut = listTanggalKeluarInt[1]
                
                tahunOut = listTanggalKeluarInt[2]

                formatOut = datetime.date(tahunOut, bulanOut, tanggalOut)
                selisihHari = formatOut - formatIn
                biaya = selisihHari * 40000
                print('''\n{} sudah ada di gudang selama {} hari, dengan total biaya simpan sebesar Rp.{}'''.format(dataGudang[index]['Nama'], selisihHari.days, biaya.days))
                break

            elif angka == '2' :
                tanggalSekarang = datetime.date.today()
                selisihHari = tanggalSekarang - formatIn
                biaya = selisihHari * 40000
                print('''\n{} sudah ada di gudang selama {} hari, dengan total biaya simpan sebesar Rp.{}'''.format(dataGudang[index]['Nama'], selisihHari.days, biaya.days))
                break
        
        break
       
   
#Function In and Out

def optionInOut() : # Untuk menampilkan menu in and out
    hasilInOut = input('''
    In and Out Sub Menu:
    1. In (Barang masuk)
    2. Out (Barang keluar)
    3. Kembali
    Silahkan masukan angka yang ingin dijalankan: ''')
    return hasilInOut

def operasiInOut(x) : # Untuk mengoperasikan in and out

    while True :
        seluruhData(dataGudang)
        
        nomor = int(input('\nInput kode barang: '))

        hasilCari = cariDataExist(nomor, 'Kode') 
        kondisi = hasilCari[0] 
        index = hasilCari[1] 

        while kondisi == True :
            
            angka = int(input('Berapa kuantitas {}: '.format(dataGudang[index]['Nama'])))

            if x == '1':
                dataGudang[index]['Stock'] += angka
                print('\nDATA SUCCESSFULLY UPDATE!')
                break 

            elif x == '2' :

                if angka > dataGudang[index]['Stock'] :
                    print('\n STOCK KURANG!')
                    break

                dataGudang[index]['Stock'] -= angka
                print('\nDATA SUCCESSFULLY UPDATE!')
                break
        
        break

#Function Menu Utama

def menuUtama () : # Untuk menampilkan menu utama program

    mainMenu = input('''
    ----------------Welcome-------------------
    -------------Applikasi Gudang-------------
    Main menu:
    1. Read data
    2. Create data
    3. Update data
    4. Delete data
    5. Holding cost
    6. In and Out
    7. Exit program
    
    Silahkan input nomor plihan main menu: ''')

    return mainMenu

# Mulai Aplikasi
while True :
    
    hasilPilihMenu = menuUtama()

    if hasilPilihMenu == '1' :
        while True :
            reading = optionReading()
            if reading == '1':
                seluruhData(dataGudang)
                continue
            elif reading == '2' :
                dataTertentu()
            elif reading == '3' :
                balik = balikMainMenu()
                if balik == 'yes' :
                    break
                else :
                    continue
            else :
                print('\n INPUT SALAH!')
                continue
                      
    elif hasilPilihMenu == '2' :
        while True :
            creating = optionCreate()
            if creating == '1' :
                tambahData()
            elif creating == '2' :
                balik = balikMainMenu()
                if balik == 'yes' :
                    break
                else :
                    continue
            else :
                print('\n INPUT SALAH!')
                continue
    
    elif hasilPilihMenu == '3' :
        while True :
            update = optionUpdate()
            if update == '1' :
                updateData()
            elif update == '2' :
                balik = balikMainMenu()
                if balik == 'yes' :
                    break
                else :
                    continue
            else :
                print('\n INPUT SALAH!')
                continue

    elif hasilPilihMenu == '4' :
        while True :
            delete = optionDelete()
            if delete == '1' :
                deleteData()
            elif delete == '2' :
                balik = balikMainMenu()
                if balik == 'yes' :
                    break
                else :
                    continue
            else :
                print('\n INPUT SALAH!')
                continue

    elif hasilPilihMenu == '5' :
        while True :
            holding = optionHoldingCost()
            if holding == '1' :
                holdingCost('1')
                continue
            elif holding == '2' :
                holdingCost('2')
                continue
            elif holding == '3' :
                balik = balikMainMenu()
                if balik == 'yes' :
                    break
                else :
                    continue
            else : 
                print('\n INPUT SALAH!')
                continue

    elif hasilPilihMenu == '6' :
        while True :
            InOut = optionInOut()
            if InOut == '1' :
                operasiInOut('1')
                continue
            elif InOut == '2' :
                operasiInOut('2')
                continue
            elif InOut == '3':
                balik = balikMainMenu()
                if balik == 'yes' :
                    break
                else :
                    continue
            else : 
                print('\n INPUT SALAH!')
                continue

    elif hasilPilihMenu == '7' :
        print('\n APLIKASI BERHENTI')
        break

    else :
        print('\n THE OPTION YOU ENTERED IS NOT VALID!')
        continue

    
   
