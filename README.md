# normal-vector-cal
import random
# 3 tane x y z kordinatına sahip nokta oluşucak
# main fonksiyoda 3 tane empty list  tanımla daha sonra initialize fonksiyonunu çağır
def main():
    P1=[]
    P2=[]
    P3=[]
    initializeCoordinates(P1,P2,P3)
    print("coordinates for p1")
    print(P1)
    print("coordinates for p2")
    print(P2)
    print("coordinates for p3")
    print(P3)
    nV=calculateNormaLs(P1, P2, P3) # FONK içinde mainden farklı isimlendirme yapılır
    print("normal vector")
    print(nV) #fonksiyon içinde hesplananı mainde yazdırırız
    ang=calculateAngels(nV)
    print("angle vector")
    for i in range(0,3):
        print(format(ang[i],"3.6"),end=" ")
    if isSameSurface(ang,5):
        print("same surface")
    else:
        print("not in same surface")
        
# her bir listenin her bir coordinatına  7 ile 15 arasında rakam atıycak
def initializeCoordinates(p1,p2,p3):
    for i in range(0,3): #x,y,z koordinatları aldı 0 . 1. 2. eleman olarak
    p1.append(random.randint(7,16))
    p2.append(random.randint(7,16))
    p3.append(random.randint(7,16))

#coordinatların x y z lerini verilen formule göre hesaplancak x 0. index y 1.index
#def cal normals fonksiyonu içinde yapılcak işlemler
def calculateNormaLs(p1,p2,p3):
    temp=[] #boş bir liste tanımla verilen formüle göre 3 noktadan bir normal vektör çıkıcak
    #temp listesinin içine atıncak işlem sonuçları
    temp.append((p2[1]-p1[1])*(p3[2]-p1[2])-(p2[2]-p1[2])*(p3[1]-p1[1]))
    temp.append((p2[2]-p1[2])*(p3[0]-p1[0])-(p2[0]-p1[0])*(p3[2]-p1[2]))
    temp.append((p2[0]-p1[0])*(p3[1]-p1[1])-(p2[1]-p1[1])*(p3[0]-p1[0]))
    retun temp
#calculate angels diye fonksiyon yaz nu normal vektörü alsın retrun olarak angle vektör döndürsün
def calculateAngels(v):#nv değerini fonksiyon içine farklı isimle atamak zorunda olduğumuzdan v dedik
    temp=[]
    temp.append(math.degrees(math.acos(v[0]/math.sqrt(v[0]**2+v[1]**2)+v[2]**2)))
    temp.append(math.degrees(math.acos(v[1]/math.sqrt(v[0]**2+v[1]**2)+v[2]**2)))
    temp.append(math.degrees(math.acos(v[2]/math.sqrt(v[0]**2+v[1]**2)+v[2]**2)))
    return temp
def isSameSurface(a,t) # a angle t threshold değerlerini tutar
    if math.fabs(a[0]-a[2]<t and math.fabs(a[0]-a[2])<t and math.fabs(a[1]-a[2])<t):
        return True
    else:
        return False
main()
