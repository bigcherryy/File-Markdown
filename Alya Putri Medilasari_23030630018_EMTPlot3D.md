Nama : Alya Putri Medilasari

NIM  : 23030630018

Kelas: Matematika B 2023

## Menggambar Plot 3D dengan EMT 

Ini adalah pengenalan plot 3D di Euler. Kami membutuhkan plot 3D untuk memvisualisasikan fungsi dari dua variabel.

Euler menggambar fungsi seperti itu menggunakan algoritma pengurutan untuk menyembunyikan bagian di latar belakang. Secara umum, Euler menggunakan proyeksi pusat. Defaultnya adalah dari kuadran x-y positif ke arah asal x = y = z = 0, tetapi sudut = 0 ? melihat dari arah sumbu y. Sudut pandang dan ketinggian dapat diubah.

Euler bisa merencanakan
* permukaan dengan bayangan dan garis level atau rentang level,
* awan poin,
* kurva parametrik,
* permukaan implisit.

Plot 3D dari suatu fungsi menggunakan plot3d. Cara termudah adalah dengan memplot ekspresi dalam x dan y. Parameter r mengatur kisaran plot sekitar (0,0).

\>aspect(1.5); plot3d("x^2+sin(y)",-5,5,0,6\*pi):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-001.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-001.png)

# Fungsi Dua Variabel

Untuk grafik suatu fungsi, gunakan
* ekspresi sederhana dalam x dan y,
* nama fungsi dari dua variabel l
* atau matriks data.

Defaultnya adalah kisi kawat yang diisi dengan warna berbeda di kedua sisi. Perhatikan bahwa jumlah default interval kisi adalah 10, tetapi plot menggunakan jumlah default persegi panjang 40x40 untuk membuat
permukaan. Ini bisa diubah.

* n = 40, n = [40,40]: jumlah garis grid di setiap arah
* grid= 10, grid = [10,10]: jumlah garis kisi di setiap arah.

Kami menggunakan default n = 40 dan grid = 10.

\>plot3d("x^2+y^2"):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-002.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-002.png)

Interaksi pengguna dimungkinkan dengan&gt; user parameter. Pengguna dapat menekan tombol berikut.

* left,right,up,down: putar sudut pandang
* +, -: memperbesar atau memperkecil
* a: menghasilkan anaglyph (lihat di bawah)
* l: beralih memutar sumber cahaya (lihat di bawah)
* space: reset ke default
* return: interaksi akhir

\>plot3d("exp(-x^2+y^2)",\>user, ...  

\>     title="Turn with the vector keys (press return to finish)"):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-003.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-003.png)

Rentang plot untuk fungsi dapat ditentukan dengan
* a, b: rentang-x
* c, d: rentang y
* r: persegi simetris di sekitar (0,0).
* n: jumlah subinterval untuk plot.

Ada beberapa parameter untuk menskalakan fungsi atau mengubah tampilan grafik.

fscale: menskalakan ke nilai fungsi (defaultnya adalah &lt;fscale).

scale: angka atau vektor 1x2 untuk skala ke arah x dan y.

frame: jenis bingkai (default 1)

\>plot3d("exp(-(x^2+y^2)/5)",r=10,n=80,fscale=4,scale=1.2,frame=3,\>user):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-004.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-004.png)

Tampilan dapat diubah dengan berbagai cara.
* distance: jarak pandang ke plot.
* zoom: nilai zoom.
* angle: sudut ke sumbu y negatif dalam radian.
* height: ketinggian tampilan dalam radian.

Nilai default bisa diperiksa atau diubah dengan fungsi view (). Ini mengembalikan parameter dalam urutan di atas.

\>view

    [5,  2.6,  2,  0.4]

Jarak yang lebih dekat membutuhkan lebih sedikit zoom. Efeknya lebih seperti lensa sudut lebar.

Dalam contoh berikut, sudut = 0 dan tinggi = 0 dilihat dari sumbu y negatif. Label sumbu untuk y disembunyikan dalam kasus ini.

\>plot3d("x^2+y",distance=3,zoom=1,angle=pi/2,height=0):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-005.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-005.png)

Plot selalu terlihat ke tengah plot kubus. Anda dapat memindahkan
pusat dengan parameter tengah.


\>plot3d("x^4+y^2",a=0,b=1,c=-1,d=1,angle=-20°,height=20°, ...  
\>     center=[0.4,0,0],zoom=5):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-006.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-006.png)

Plot diskalakan agar sesuai dengan kubus satuan untuk dilihat. Jadi tidak perlu mengubah jarak atau zoom tergantung ukuran plot. Namun, label mengacu pada ukuran sebenarnya.

Jika Anda mematikannya dengan scale = false, Anda harus berhati-hati, bahwa plot masih pas dengan jendela plotting, dengan mengubah jarak pandang atau zoom, dan memindahkan pusat.

\>plot3d("5\*exp(-x^2-y^2)",r=2,<fscale,<scale,distance=13,height=50°, ...  

\>     center=[0,0,-2],frame=3):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-007.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-007.png)
Plot kutub juga tersedia. The parameter polar= true menggambarkan plot kutub. Fungsi tersebut harus tetap merupakan fungsi dari x dan y. Parameter "fscale" menskalakan fungsi dengan skala sendiri. Jika tidak, fungsi diskalakan agar sesuai dengan kubus.

\>plot3d("1/(x^2+y^2+1)",r=5,\>polar, ...  
\>   fscale=2,\>hue,n=100,zoom=4,\>contour,color=blue):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-008.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-008.png)

\>function f(r) := exp(-r/2)\*cos(r); ...  
\>   plot3d("f(x^2+y^2)",\>polar,scale=[1,1,0.4],r=pi,frame=3,zoom=4):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-009.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-009.png)

Parameter memutar memutar fungsi dalam x di sekitar sumbu x.
* rotate = 1: Menggunakan sumbu x
* rotate = 2: Menggunakan sumbu z
  
\>plot3d("x^2+1",a=-1,b=1,rotate=true,grid=5):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-010.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-010.png)

\>plot3d("x^2+1",a=-1,b=1,rotate=2,grid=5):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-011.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-011.png)

\>plot3d("sqrt(25-x^2)",a=0,b=5,rotate=1):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-012.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-012.png)

\>plot3d("x\*sin(x)",a=0,b=6pi,rotate=2):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-013.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-013.png)
Ini adalah plot dengan tiga fungsi

\>plot3d("x","x^2+y^2","y",r=2,zoom=3.5,frame=3):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-014.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-014.png)

# Plot Kontur

Untuk plot, Euler menambahkan garis kisi. Alih-alih, dimungkinkan untuk menggunakan garis level dan corak satu warna atau corak warna spektral. Euler dapat menggambar ketinggian fungsi pada plot dengan shading. Di semua plot 3D, Euler dapat menghasilkan anaglyph merah / cyan.

-&gt; hue: Mengaktifkan bayangan terang, bukan kabel.
-&gt; contour: Membuat plot garis kontur otomatis pada plot.
- level = ... (atau level): Vektor nilai untuk garis kontur.

Standarnya adalah level = "auto", yang menghitung beberapa baris level secara otomatis. Seperti yang Anda lihat di plot, level sebenarnya adalah rentang level.

Gaya default dapat diubah. Untuk plot kontur berikut, kami menggunakan kisi yang lebih halus untuk 100x100 titik, menskalakan fungsi dan plot, dan menggunakan sudut pandang yang berbeda.

\>plot3d("exp(-x^2-y^2)",r=2,n=100,level="thin", ...  
\>    \>contour,\>spectral,fscale=1,scale=1.1,angle=45°,height=20°):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-015.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-015.png)

\>plot3d("exp(x\*y)",angle=100°,\>contour,color=green):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-016.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-016.png)

Bayangan default menggunakan warna abu-abu. Tetapi berbagai spektrum warna juga tersedia.

-&gt; spectral: Menggunakan skema spektral default
- color = ...: Menggunakan warna khusus atau skema spektral
  
Untuk plot berikut, kami menggunakan skema spektral default dan menambah jumlah poin untuk mendapatkan tampilan yang sangat mulus.

\>plot3d("x^2+y^2",\>spectral,\>contour,n=100):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-017.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-017.png)
Alih-alih garis level otomatis, kami juga dapat mengatur nilai garis level. Ini akan menghasilkan garis level tipis, bukan rentang level.

\>plot3d("x^2-y^2",0,5,0,5,level=-1:0.1:1,color=redgreen):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-018.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-018.png)
Dalam plot berikut, kami menggunakan dua pita level yang sangat luas dari -0,1 hingga 1, dan dari 0,9 hingga 1. Ini dimasukkan sebagai
matriks dengan batas level sebagai kolom.

Selain itu, kami melapisi kisi dengan 10 interval di setiap arah.

\>plot3d("x^2+y^3",level=[-0.1,0.9;0,1], ...  
\>     \>spectral,angle=30°,grid=10,contourcolor=gray):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-019.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-019.png)

Dalam contoh berikut, kami memplot set, di mana

Kami menggunakan satu garis tipis untuk garis level.

\>plot3d("x^y-y^x",level=0,a=0,b=6,c=0,d=6,contourcolor=red,n=100):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-020.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-020.png)

Dimungkinkan untuk menunjukkan bidang kontur di bawah plot. Warna dan jarak ke plot dapat ditentukan.

\>plot3d("x^2+y^4",\>cp,cpcolor=green,cpdelta=0.2):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-021.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-021.png)

Berikut beberapa gaya lainnya. Kami selalu mematikan bingkai, dan
menggunakan berbagai skema warna untuk plot dan kisi.

\>figure(2,2); ...  
\>   expr="y^3-x^2"; ...  
\>   figure(1);  ...  
\>     plot3d(expr,<frame,\>cp,cpcolor=spectral); ...  
\>   figure(2);  ...  
\>     plot3d(expr,<frame,\>spectral,grid=10,cp=2); ...  
\>   figure(3);  ...  
\>     plot3d(expr,<frame,\>contour,color=gray,nc=5,cp=3,cpcolor=greenred); ...  
\>   figure(4);  ...  
\>     plot3d(expr,<frame,\>hue,grid=10,\>transparent,\>cp,cpcolor=gray); ...  
\>   figure(0):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-022.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-022.png)

Ada beberapa skema spektral lain, diberi nomor dari 1 hingga 9. Tetapi
Anda juga dapat menggunakan color=value, di mana nilai

* spectral: untuk rentang dari biru hingga merah
* white: untuk rentang yang lebih redup
* yellowblue,purplegreen,blueyellow,greenred
* blueyellow, greenpurple,yellowblue,redgreen

\>figure(3,3); ...  
\>   for i=1:9;  ...  
\>     figure(i); plot3d("x^2+y^2",spectral=i,\>contour,\>cp,<frame,zoom=4);  ...  
\>   end; ...  
\>   figure(0):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-023.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-023.png)

Sumber cahaya dapat diubah dengan l dan tombol kursor selama interaksi
pengguna. Itu juga dapat diatur dengan parameter.

- light : arah cahaya
- amb: cahaya ambient antara 0 dan 1

Perhatikan bahwa program tidak membuat perbedaan antara sisi-sisi plot. Tidak ada bayangan. Untuk ini, Anda membutuhkan Povray.

\>plot3d("-x^2-y^2", ...  
\>     hue=true,light=[0,1,1],amb=0,user=true, ...  
\>     title="Press l and cursor keys (return to exit)"):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-024.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-024.png)
Parameter warna mengubah warna permukaan. Warna garis level juga dapat diubah.

\>plot3d("-x^2-y^2",color=rgb(0.2,0.2,0),hue=true,frame=false, ...  
\>     zoom=3,contourcolor=red,level=-2:0.1:1,dl=0.01):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-025.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-025.png)

Warna 0 memberikan efek pelangi khusus.

\>plot3d("x^2/(x^2+y^2+1)",color=0,hue=true,grid=10):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-026.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-026.png)

Permukaannya juga bisa transparan.

\>plot3d("x^2+y^2",\>transparent,grid=10,wirecolor=red):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-027.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-027.png)

# Plot Implisit

Ada juga plot implisit dalam tiga dimensi. Euler menghasilkan pemotongan melalui objek. Fitur plot3d termasuk plot implisit. Plot ini menunjukkan himpunan nol fungsi dalam tiga variabel.

Solusi dari
$$f(x,y,z) = 0$$dapat divisualisasikan dalam potongan sejajar dengan bidang x-y-,
x-z-, dan y-z.


* implisit = 1: potong sejajar bidang y-z
* implisit = 2: potong sejajar dengan bidang x-z
* implisit = 4: potong sejajar bidang x-y

Tambahkan nilai-nilai ini, jika Anda suka. Dalam contoh yang kami plot
$$M = \{ (x,y,z) : x^2+y^3+zy=1 \}$$\>plot3d("x^2+y^3+z\*y-1",r=5,implicit=3):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-030.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-030.png)
\>c=1; d=1;

\>plot3d("((x^2+y^2-c^2)^2+(z^2-1)^2)\*((y^2+z^2-c^2)^2+(x^2-1)^2)\*((z^2+x^2-c^2)^2+(y^2-1)^2)-d",r=2,<frame,\>implicit,\>user):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-031.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-031.png)
\>plot3d("x^2+y^2+4\*x\*z+z^3",\>implicit,r=2,zoom=2.5):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-032.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-032.png)

# Plotting 3D Data

Sama seperti plot2d, plot3d menerima data. Untuk objek 3D, Anda perlu
memberikan matriks nilai x, y dan z, atau tiga fungsi atau ekspresi fx
(x, y), fy (x, y), fz (x, y).
$$\gamma(t,s) = (x(t,s),y(t,s),z(t,s))$$Karena x, y, z adalah matriks, kita asumsikan bahwa (t, s) berjalan melalui kotak persegi. Hasilnya, Anda dapat memplot gambar persegi
panjang di luar angkasa.

Anda dapat menggunakan bahasa matriks Euler untuk menghasilkankoordinat secara efektif.

Dalam contoh berikut, kami menggunakan vektor nilai t dan vektor kolom nilai s untuk membuat parameter permukaan bola. Dalam gambar kita bisa menandai daerah, dalam kasus kita daerah kutub.

\>t=linspace(0,2pi,180); s=linspace(-pi/2,pi/2,90)'; ...  
\>   x=cos(s)\*cos(t); y=cos(s)\*sin(t); z=sin(s); ...  
\>   plot3d(x,y,z,\>hue, ...  
\>   color=blue,<frame,grid=[10,20], ...  
\>   values=s,contourcolor=red,level=[90°-24°;90°-22°], ...  
\>   scale=1.4,height=50°):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-034.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-034.png)

Berikut adalah contoh grafik dari suatu fungsi.

\>t=-1:0.1:1; s=(-1:0.1:1)'; plot3d(t,s,t\*s,grid=10):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-035.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-035.png)
Namun, kita bisa membuat semua jenis permukaan. Ini adalah permukaan yang sama sebagai suatu fungsi

\>plot3d(t\*s,t,s,angle=180°,grid=10):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-036.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-036.png)

Dengan lebih banyak usaha, kami dapat menghasilkan banyak permukaan.

Dalam contoh berikut, kami membuat tampilan berbayang dari bola yang terdistorsi. Koordinat biasa untuk bola adalah dengan
Kami menyimpangkan ini dengan sebuah faktor

\>t=linspace(0,2pi,320); s=linspace(-pi/2,pi/2,160)'; ...  
\>   d=1+0.2\*(cos(4\*t)+cos(8\*s)); ...  
\>   plot3d(cos(t)\*cos(s)\*d,sin(t)\*cos(s)\*d,sin(s)\*d,hue=1, ...  
\>     light=[1,0,1],frame=0,zoom=5):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-037.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-037.png)

Tentu saja, point cloud juga dimungkinkan. Untuk memplot data titik
dalam ruang, kita membutuhkan tiga vektor sebagai koordinat titik.

Gayanya sama seperti di plot2d dengan points = true;

\>n=500;  ...  
\>     plot3d(normal(1,n),normal(1,n),normal(1,n),points=true,style="."):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-038.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-038.png)
Juga dimungkinkan untuk memplot kurva dalam 3D. Dalam kasus ini, lebih mudah untuk menghitung sebelumnya titik-titik kurva. Untuk kurva di bidang kita menggunakan urutan koordinat dan parameter wire = true.

\>t=linspace(0,8pi,500); ...  
\>   plot3d(sin(t),cos(t),t/10,\>wire,zoom=3):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-039.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-039.png)
\>t=linspace(0,4pi,1000); plot3d(cos(t),sin(t),t/2pi,\>wire, ...  
\>   linewidth=3,wirecolor=blue):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-040.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-040.png)
\>X=cumsum(normal(3,100)); ...  
\>    plot3d(X[1],X[2],X[3],\>anaglyph,\>wire):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-041.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-041.png)
EMT juga dapat memplot dalam mode anaglyph. Untuk melihat plot seperti
itu, Anda membutuhkan red/cyan glasses.

\> plot3d("x^2+y^3",\>anaglyph,\>contour,angle=30°):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-042.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-042.png)
Seringkali, skema warna spektral digunakan untuk plot. Ini menekankan
ketinggian fungsinya.


\>plot3d("x^2\*y^3-y",\>spectral,\>contour,zoom=3.2):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-043.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-043.png)

Euler juga dapat memplot permukaan berparameter, jika parameternya adalah nilai x, y, dan z dari gambar kisi persegi panjang di dalam
ruang.

Untuk demo berikut, kami menyiapkan parameter u- dan v-, dan menghasilkan koordinat ruang dari ini.

\>u=linspace(-1,1,10); v=linspace(0,2\*pi,50)'; ...  
\>   X=(3+u\*cos(v/2))\*cos(v); Y=(3+u\*cos(v/2))\*sin(v); Z=u\*sin(v/2); ...  
\>   plot3d(X,Y,Z,\>anaglyph,<frame,\>wire,scale=2.3):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-044.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-044.png)

Berikut adalah contoh yang lebih rumit, yang megah dengan red/cyan glasses.

\>u:=linspace(-pi,pi,160); v:=linspace(-pi,pi,400)';  ...  
\>   x:=(4\*(1+.25\*sin(3\*v))+cos(u))\*cos(2\*v); ...  
\>   y:=(4\*(1+.25\*sin(3\*v))+cos(u))\*sin(2\*v); ...  
\>    z=sin(u)+2\*cos(3\*v); ...  
\>   plot3d(x,y,z,frame=0,scale=1.5,hue=1,light=[1,0,-1],zoom=2.8,\>anaglyph):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-045.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-045.png)

** Plot Statistik

Plot batang juga dimungkinkan. Untuk ini, kami harus menyediakan

* x: vektor baris dengan n + 1 elemen
* y: vektor kolom dengan n + 1 elemen
* z: nxn matriks nilai.

z bisa lebih besar, tetapi hanya nilai nxn yang akan digunakan.

Dalam contoh, pertama-tama kita menghitung nilainya. Kemudian kita menyesuaikan x dan y, sehingga vektor berpusat pada nilai yang
digunakan.

\>x=-1:0.1:1; y=x'; z=x^2+y^2; ...  
\>   xa=(x|1.1)-0.05; ya=(y\_1.1)-0.05; ...  
\>   plot3d(xa,ya,z,bar=true):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-046.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-046.png)

Dimungkinkan untuk membagi plot permukaan menjadi dua bagian atau lebih.
 
\>x=-1:0.1:1; y=x'; z=x+y; d=zeros(size(x)); ...  
\>   plot3d(x,y,z,disconnect=2:2:20):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-047.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-047.png)

Jika memuat atau membuat matriks data M dari file dan perlu memplotnya dalam 3D, Anda dapat menskalakan matriks ke [-1,1] dengan skala (M), atau menskalakan matriks dengan&gt; zscale. Ini dapat dikombinasikan
dengan faktor penskalaan individu yang diterapkan sebagai tambahan.

\>i=1:20; j=i'; ...  
\>   plot3d(i\*j^2+100\*normal(20,20),\>zscale,scale=[1,1,1.5],angle=-40°,zoom=1.8):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-048.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-048.png)

\>Z=intrandom(5,100,6); v=zeros(5,6); ...  
\>   loop 1 to 5; v[#]=getmultiplicities(1:6,Z[#]); end; ...  
\>   columnsplot3d(v',scols=1:5,ccols=[1:5]):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-049.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-049.png)

# Permukaan Benda Putar

\>plot2d("(x^2+y^2-1)^3-x^2\*y^3",r=1.3, ...  
\>   style="#",color=red,<outline, ...  
\>   level=[-2;0],n=100):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-050.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-050.png)

\>ekspresi &= (x^2+y^2-1)^3-x^2\*y^3; $ekspresi
$$\left(y^2+x^2-1\right)^3-x^2\,y^3$$Kami ingin memutar kurva jantung di sekitar sumbu y. Inilah ungkapan yang mendefinisikan hati:

Selanjutnya kita atur

\>function fr(r,a) &= ekspresi with [x=r\*cos(a),y=r\*sin(a)] | trigreduce; $fr(r,a)
$$\left(r^2-1\right)^3+\frac{\left(\sin \left(5\,a\right)-\sin \left(  3\,a\right)-2\,\sin a\right)\,r^5}{16}$$Hal ini memungkinkan untuk menentukan fungsi numerik, yang menyelesaikan r, jika a diberikan. Dengan fungsi itu kita dapat
memplot jantung yang berubah sebagai permukaan parametrik.

\>function map f(a) := bisect("fr",0,2;a); ...  
\>   t=linspace(-pi/2,pi/2,100); r=f(t);  ...  
\>   s=linspace(pi,2pi,100)'; ...  
\>   plot3d(r\*cos(t)\*sin(s),r\*cos(t)\*cos(s),r\*sin(t), ...  
\>   \>hue,<frame,color=red,zoom=4,amb=0,max=0.7,grid=12,height=50°):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-053.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-053.png)
Berikut ini adalah plot 3D dari gambar di atas yang diputar di sekitar
sumbu z. Kami mendefinisikan fungsi, yang mendeskripsikan objek.

\>function f(x,y,z) ...


    r=x^2+y^2;
    return (r+z^2-1)^3-r*z^3;
     endfunction

\>plot3d("f(x,y,z)", ...  
\>   xmin=0,xmax=1.2,ymin=-1.2,ymax=1.2,zmin=-1.2,zmax=1.4, ...  
\>   implicit=1,angle=-30°,zoom=2.5,n=[10,60,60],\>anaglyph):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-054.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-054.png)

# Special 3D Plots

Fungsi plot3d bagus untuk dimiliki, tetapi tidak memenuhi semua kebutuhan. Selain rutinitas yang lebih mendasar, Anda bisa mendapatkan plot berbingkai dari objek apa pun yang Anda suka.

Meskipun Euler bukan program 3D, Euler dapat menggabungkan beberapa objek dasar. Kami mencoba untuk memvisualisasikan paraboloid dan garis singgung-nya.

\>function myplot ...

      y=0:0.01:1; x=(0.1:0.01:1)';
      plot3d(x,y,0.2*(x-0.1)/2,<scale,<frame,>hue, ..
        hues=0.5,>contour,color=orange);
      h=holding(1);
      plot3d(x,y,(x^2+y^2)/2,<scale,<frame,>contour,>hue);
      holding(h);
    endfunction

Sekarang framedplot () menyediakan bingkai, dan menyetel tampilan.
\>framedplot("myplot",[0.1,1,0,1,0,1],angle=-45°, ...  
\>     center=[0,0,-0.7],zoom=6):
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-055.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-055.png)

Dengan cara yang sama, Anda dapat memplot bidang kontur secara manual.
Perhatikan bahwa plot3d () menyetel jendela ke fullwindow () secara
default, tetapi plotcontourplane () mengasumsikannya.


\>x=-1:0.02:1.1; y=x'; z=x^2-y^4;

\>function myplot (x,y,z) ...  
\>  
<pre class="udf">      zoom(2);
      wi=fullwindow();
      plotcontourplane(x,y,z,level="auto",<scale);
      plot3d(x,y,z,>hue,<scale,>add,color=white,level="thin");
      window(wi);
      reset();
    endfunction
</pre>
\>myplot(x,y,z):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-056.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-056.png)

# Animasi

Salah satu fungsi yang memanfaatkan teknik ini adalah memutar. Itu dapat mengubah sudut pandang dan menggambar ulang plot 3D. Fungsi tersebut memanggil addpage () untuk setiap plot baru. Akhirnya itu
menjiwai plot.

Harap pelajari sumber rotasi untuk melihat lebih detail.

\>function testplot () := plot3d("x^2+y^3"); ...  
\>   rotate("testplot"); testplot():


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-057.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-057.png)

# Menggambar Povray

Dengan bantuan file Euler povray.e, Euler dapat menghasilkan file Povray. Hasilnya sangat bagus untuk dilihat.

Anda perlu menginstal Povray (32bit atau 64bit)dari

  <a href="http://www.povray.org/,">http://www.povray.org/,</a>

dan meletakkan sub-direktori "bin" Povray ke dalam jalur lingkungan, atau menyetel variabel "defaultpovray" dengan jalur lengkap yang
mengarah ke "pvengine.exe".

Antarmuka Povray dari Euler menghasilkan file Povray di direktori home pengguna, dan memanggil Povray untuk mengurai file-file ini. Nama file default adalah current.pov, dan direktori default adalah eulerhome (), biasanya c: \ Users \ Username \ Euler. Povray menghasilkan file PNG, yang dapat dimuat oleh Euler ke dalam notebook. Untuk membersihkan
file-file ini, gunakan povclear ().

Fungsi pov3d memiliki semangat yang sama dengan plot3d. Ini dapat menghasilkan grafik fungsi f (x, y), atau permukaan dengan koordinat X, Y, Z dalam matriks, termasuk garis level opsional. Fungsi ini memulai raytracer secara otomatis, dan memuat pemandangan ke dalam notebook Euler.

Selain pov3d (), ada banyak fungsi yang menghasilkan objek Povray. Fungsi-fungsi ini mengembalikan string, berisi kode Povray untuk
objek. Untuk menggunakan fungsi ini, mulai file Povray dengan povstart (). Kemudian gunakan writeln (...) untuk menulis objek ke file adegan. Terakhir, akhiri file dengan povend (). Secara default, raytracer akan mulai, dan PNG akan dimasukkan ke dalam notebook Euler.


Fungsi objek memiliki parameter yang disebut "look", yang membutuhkan string dengan kode Povray untuk tekstur dan penyelesaian objek. Fungsi\ povlook () dapat digunakan untuk menghasilkan string ini. Ini memiliki parameter untuk warna, transparansi, Phong Shading dll. 

Perhatikan bahwa alam semesta Povray memiliki sistem koordinat lain. Antarmuka ini menerjemahkan semua koordinat ke sistem Povray. Jadi Anda dapat terus berpikir dalam sistem koordinat Euler dengan z menunjuk ke atas secara vertikal, sumbu a nd x, y, z di tangan kanan.

Anda perlu memuat file povray.

\>load povray;

Pastikan, direktori bin Povray ada di jalurnya. Jika tidak, edit variabel berikut sehingga berisi path ke povray yang dapat dieksekusi.
 
\>defaultpovray="C:\\Program Files\\POV-Ray\\v3.7\\bin\\pvengine.exe"

    C:\Program Files\POV-Ray\v3.7\bin\pvengine.exe

Untuk pertamakali, kami memplot fungsi sederhana. Perintah berikut menghasilkan file povray di direktori pengguna Anda, dan menjalankan Povray untuk menelusuri file ini.
 
Jika Anda memulai perintah berikut, GUI Povray akan terbuka,
menjalankan file, dan menutup secara otomatis. Karena alasan keamanan,
Anda akan ditanya, apakah Anda ingin mengizinkan file exe dijalankan.
Anda dapat menekan batal untuk menghentikan pertanyaan lebih lanjut.
Anda mungkin harus menekan OK di jendela Povray untuk mengetahui
dialog start-up Povray. 

\>plot3d("x^2+y^2",zoom=2):
 
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-058.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-058.png)

\>pov3d("x^2+y^2",zoom=3);
 
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-059.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-059.png)
 

Kita bisa membuat fungsinya transparan dan menambahkan hasil akhir lainnya. Kita juga bisa menambahkan garis level ke plot fungsi.

\>pov3d("x^2+y^3",axiscolor=red,angle=-45°,\>anaglyph, ...  
\>     look=povlook(cyan,0.2),level=-1:0.5:1,zoom=3.8);


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-060.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-060.png)

Terkadang perlu untuk mencegah penskalaan fungsi, dan menskalakan fungsi dengan tangan.


Kami memplot himpunan titik di bidang kompleks, di mana hasil kali
jarak ke 1 dan -1 sama dengan 1.

\>pov3d("((x-1)^2+y^2)\*((x+1)^2+y^2)/40",r=1.5, ...  
\>     angle=-120°,level=1/40,dlevel=0.005,light=[-1,1,1],height=45°,n=50, ...  
\>     <fscale,zoom=3.8);


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-061.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-061.png)

# Merencanakan dengan Koordinat

Alih-alih fungsi, kita bisa memplot dengan koordinat. Seperti pada plot3d, kita membutuhkan tiga matriks untuk mendefinisikan objeknya.

Dalam contoh ini, kita memutar fungsi di sekitar sumbu z.

\>function f(x) := x^3-x+1; ...  
\>   x=-1:0.01:1; t=linspace(0,2pi,8)'; ...  
\>   Z=x; X=cos(t)\*f(x); Y=sin(t)\*f(x); ...  
\>   pov3d(X,Y,Z,angle=40°,height=20°,axis=0,zoom=4,light=[10,-5,5]);


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-062.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-062.png)

Dalam contoh berikut, kami memplot gelombang teredam. Kami menghasilkan gelombang dengan bahasa matriks Euler.

Kami juga menunjukkan, bagaimana objek tambahan dapat ditambahkan ke adegan pov3d. Untuk pembuatan objek, lihat contoh berikut. Perhatikan bahwa plot3d menskalakan plot, sehingga sesuai dengan kubus satuan

\>r=linspace(0,1,80); phi=linspace(0,2pi,80)'; ...  
\>   x=r\*cos(phi); y=r\*sin(phi); z=exp(-5\*r)\*cos(8\*pi\*r)/3;  ...  
\>   pov3d(x,y,z,zoom=5,axis=0,add=povsphere([0,0,0.5],0.1,povlook(green)), ...  
\>     w=500,h=300);


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-063.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-063.png)

Dengan metode naungan lanjutan Povray, sangat sedikit titik yang dapat menghasilkan permukaan yang sangat halus. Hanya di perbatasan dan dalam bayangan, triknya mungkin menjadi jelas.

Untuk ini, kita perlu menambahkan vektor normal di setiap titik matriks.

\>Z &= x^2\*y^3

    
                                     2  3
                                    x  y
    

Persamaan permukaannya adalah [x, y, Z]. Kami menghitung dua turunan menjadi x dan y dari ini dan mengambil produk silang sebagai normal.

\>dx &= diff([x,y,Z],x); dy &= diff([x,y,Z],y);

Kami mendefinisikan normal sebagai produk silang dari turunan ini, dan mendefinisikan fungsi koordinat.\

\>N &= crossproduct(dx,dy); NX &= N[1]; NY &= N[2]; NZ &= N[3]; N,


    
                                   3       2  2
                           [- 2 x y , - 3 x  y , 1]
    

We use only 25 points.

\>x=-1:0.5:1; y=x';

\>pov3d(x,y,Z(x,y),angle=10°, ...  
\>     xv=NX(x,y),yv=NY(x,y),zv=NZ(x,y),<shadow);


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-064.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-064.png)

Berikut ini adalah simpul Trefoil yang dilakukan oleh A. Busser di Povray. Ada versi perbaikannya dalam contoh.

  <a href="Examples\Trefoil Knot.html">Trefoil Knot</a>  

Untuk tampilan yang bagus dengan tidak terlalu banyak titik, kami
menambahkan vektor normal di sini. Kami menggunakan Maxima untuk
menghitung normal bagi kami. Pertama, tiga fungsi koordinat sebagai
ekspresi simbolik.

\>X &= ((4+sin(3\*y))+cos(x))\*cos(2\*y); ...  
\>   Y &= ((4+sin(3\*y))+cos(x))\*sin(2\*y); ...  
\>   Z &= sin(x)+2\*cos(3\*y);

Kemudian dua vektor turunannya menjadi x dan y.

\>dx &= diff([X,Y,Z],x); dy &= diff([X,Y,Z],y);

Sekarang normal, yang merupakan produk persilangan dari dua
turunannya.

\>dn &= crossproduct(dx,dy);

Kami sekarang mengevaluasi semua ini secara numerik.

\>x:=linspace(-%pi,%pi,40); y:=linspace(-%pi,%pi,100)';

Vektor normal adalah evaluasi dari ekspresi simbolik dn [i] untuk i =1,2,3. Sintaks untuk ini adalah &amp; "expresi" (parameter). Ini adalahn alternatif metode pada contoh sebelumnya, di mana kita mendefinisikan
ekspresi simbolik NX, NY, NZ terlebih dahulu.

\>pov3d(X(x,y),Y(x,y),Z(x,y),axis=0,zoom=5,w=450,h=350, ...  
\>     <shadow,look=povlook(gray), ...  
\>     xv=&"dn[1]"(x,y), yv=&"dn[2]"(x,y), zv=&"dn[3]"(x,y));

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-065.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-065.png)

Kami juga dapat membuat grid dalam 3D.

\>povstart(zoom=4); ...  
\>   x=-1:0.5:1; r=1-(x+1)^2/6; ...  
\>   t=(0°:30°:360°)'; y=r\*cos(t); z=r\*sin(t); ...  
\>   writeln(povgrid(x,y,z,d=0.02,dballs=0.05)); ...  
\>   povend();


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-066.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-066.png)
Dengan povgrid (), kurva dimungkinkan.

\>povstart(center=[0,0,1],zoom=3.6); ...  
\>   t=linspace(0,2,1000); r=exp(-t); ...  
\>   x=cos(2\*pi\*10\*t)\*r; y=sin(2\*pi\*10\*t)\*r; z=t; ...  
\>   writeln(povgrid(x,y,z,povlook(red))); ...  
\>   writeAxis(0,2,axis=3); ...  
\>   povend();


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-067.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-067.png)

# Objek Povray

Di atas, kami menggunakan pov3d untuk memplot permukaan. Antarmuka povray di Euler juga dapat menghasilkan objek Povray. Objek-objek ini disimpan sebagai string di Euler, dan perlu ditulis ke file Povray.

Kami memulai output dengan povstart ().

\>povstart(zoom=4);

Pertama kita tentukan tiga silinder, dan simpan dalam string di Euler.

Fungsi povx () dll. Hanya mengembalikan vektor [1,0,0], yang bisa digunakan sebagai gantinya.

\>c1=povcylinder(-povx,povx,1,povlook(red)); ...  
\>   c2=povcylinder(-povy,povy,1,povlook(green)); ...  
\>   c3=povcylinder(-povz,povz,1,povlook(blue)); ...  
\>  
String berisi kode Povray, yang tidak perlu kita pahami pada saat itu.

\>c1

    cylinder { &lt;-1,0,0&gt;, &lt;1,0,0&gt;, 1
     texture { pigment { color rgb &lt;0.564706,0.0627451,0.0627451&gt; }  } 
     finish { ambient 0.2 } 
     }

Seperti yang Anda lihat, kami menambahkan tekstur ke objek dalam tiga warna berbeda.

Itu dilakukan oleh povlook (), yang mengembalikan string dengan kode Povray yang relevan. Kita dapat menggunakan warna Euler default, atau menentukan warna kita sendiri. Kami juga dapat menambahkan transparansi, atau mengubah cahaya sekitar.

\>povlook(rgb(0.1,0.2,0.3),0.1,0.5)

     texture { pigment { color rgbf &lt;0.101961,0.2,0.301961,0.1&gt; }  } 
     finish { ambient 0.5 } 
    
Sekarang kita mendefinisikan objek interseksi, dan menulis hasilnya ke
file.

\>writeln(povintersection([c1,c2,c3]));

Perpotongan tiga silinder sulit untuk divisualisasikan, jika Anda belum pernah melihatnya sebelumnya.

\>povend;
![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-068.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-068.png)

Fungsi berikut menghasilkan fraktal secara rekursif.

Fungsi pertama menunjukkan, bagaimana Euler menangani objek Povray sederhana. Fungsi povbox () mengembalikan string, berisi koordinat kotak, tekstur, dan hasil akhir.

\>function onebox(x,y,z,d) := povbox([x,y,z],[x+d,y+d,z+d],povlook());

\>function fractal (x,y,z,h,n) ...  
\>  
<pre class="udf">     if n==1 then writeln(onebox(x,y,z,h));
     else
       h=h/3;
       fractal(x,y,z,h,n-1);
       fractal(x+2*h,y,z,h,n-1);
       fractal(x,y+2*h,z,h,n-1);
       fractal(x,y,z+2*h,h,n-1);
       fractal(x+2*h,y+2*h,z,h,n-1);
       fractal(x+2*h,y,z+2*h,h,n-1);
       fractal(x,y+2*h,z+2*h,h,n-1);
       fractal(x+2*h,y+2*h,z+2*h,h,n-1);
       fractal(x+h,y+h,z+h,h,n-1);
     endif;
    endfunction
</pre>
\>povstart(fade=10,<shadow);

\>fractal(-1,-1,-1,2,4);

\>povend();

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-069.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-069.png)

Perbedaan memungkinkan pemotongan satu objek dari yang lain. Seperti persimpangan, ada bagian dari objek CSG Povray.

\>povstart(light=[5,-5,5],fade=10);

Untuk demonstrasi ini, kami mendefinisikan sebuah objek di Povray, daripada menggunakan string di Euler. Definisi segera ditulis ke file.

Koordinat kotak -1 berarti [-1, -1, -1].

\>povdefine("mycube",povbox(-1,1));

Kita bisa menggunakan objek ini di povobject (), yang mengembalikan string seperti biasa.

\>c1=povobject("mycube",povlook(red));

Kami menghasilkan kubus kedua, dan memutar serta menskalakannya sedikit.

\>c2=povobject("mycube",povlook(yellow),translate=[1,1,1], ...  
\>     rotate=xrotate(10°)+yrotate(10°), scale=1.2);

Kemudian kita ambil perbedaan kedua objek tersebut.

\>writeln(povdifference(c1,c2));

Sekarang tambahkan tiga sumbu.

\>writeAxis(-1.2,1.2,axis=1); ...  
\>   writeAxis(-1.2,1.2,axis=2); ...  
\>   writeAxis(-1.2,1.2,axis=4); ...  
\>   povend();

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-070.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-070.png)

# Fungsi Implisit

Povray dapat memplot himpunan di mana f (x, y, z) = 0, seperti parameter implisit di plot3d. Namun, hasilnya terlihat jauh lebih
baik.

Sintaks untuk fungsinya sedikit berbeda. Anda tidak dapat menggunakan keluaran ekspresi Maxima atau Euler.

\>povstart(angle=70°,height=50°,zoom=4);

Buat permukaan implisit. Perhatikan sintaks yang berbeda dalam ekspresi tersebut.

\>writeln(povsurface("pow(x,2)\*y-pow(y,3)-pow(z,2)",povlook(green))); ...  
\>   writeAxes(); ...  
\>   povend();

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-071.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-071.png)

# Objek Jaring

Dalam contoh ini, kami menunjukkan cara membuat objek mesh, dan menggambarnya dengan informasi tambahan.

Kami ingin memaksimalkan xy di bawah kondisi x + y = 1 dan mendemonstrasikan sentuhan tangensial dari garis level.

\>povstart(angle=-10°,center=[0.5,0.5,0.5],zoom=7);

Kami tidak dapat menyimpan objek dalam string seperti sebelumnya, karena terlalu besar. Jadi kami mendefinisikan objek dalam file Povray menggunakan #declare. Fungsi povtriangle () melakukan ini secara otomatis. Ia dapat menerima vektor normal seperti pov3d ().

Yang berikut ini mendefinisikan objek mesh, dan langsung menulisnya ke dalam file.

\>x=0:0.02:1; y=x'; z=x\*y; vx=-y; vy=-x; vz=1;

\>mesh=povtriangles(x,y,z,"",vx,vy,vz);

Sekarang kami mendefinisikan dua disk, yang akan berpotongan dengan permukaan.

\>cl=povdisc([0.5,0.5,0],[1,1,0],2); ...  
\>   ll=povdisc([0,0,1/4],[0,0,1],2);

Tulis permukaan dikurangi dua cakram.

\>writeln(povdifference(mesh,povunion([cl,ll]),povlook(green)));

Tuliskan dua persimpangan tersebut.

\>writeln(povintersection([mesh,cl],povlook(red))); ...  
\>   writeln(povintersection([mesh,ll],povlook(gray)));

Tulis titik maksimal.

\>writeln(povpoint([1/2,1/2,1/4],povlook(gray),size=2\*defaultpointsize));

Tambahkan sumbu dan selesai.

\>writeAxes(0,1,0,1,0,1,d=0.015); ...  
\>   povend();

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-072.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-072.png)
# Anaglyph di Povray
Untuk menghasilkan anaglyph untuk kacamata merah / cyan, Povray harus dijalankan dua kali dari posisi kamera yang berbeda. Ini menghasilkan dua file Povray dan dua file PNG, yang dimuat dengan fungsi
loadanaglyph ().

Tentu saja, Anda memerlukan kaca mata merah / cyan untuk melihat contoh berikut dengan benar.

Fungsi pov3d () memiliki tombol sederhana untuk menghasilkan anaglyph.

\>pov3d("-exp(-x^2-y^2)/2",r=2,height=45°,\>anaglyph, ...  
\>     center=[0,0,0.5],zoom=3.5);

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-073.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-073.png)
Jika Anda membuat adegan dengan objek, Anda perlu memasukkan pembuatan adegan ke dalam fungsi, dan menjalankannya dua kali dengan nilai yang berbeda untuk parameter anaglyph.

\>function myscene ...

      s=povsphere(povc,1);
      cl=povcylinder(-povz,povz,0.5);
      clx=povobject(cl,rotate=xrotate(90°));
      cly=povobject(cl,rotate=yrotate(90°));
      c=povbox([-1,-1,0],1);
      un=povunion([cl,clx,cly,c]);
      obj=povdifference(s,un,povlook(red));
      writeln(obj);
      writeAxes();
    endfunction
</pre>
Fungsi povanaglyph () melakukan semua ini. Parameternya seperti di
povstart () dan povend () digabungkan.

\>povanaglyph("myscene",zoom=4.5);


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-074.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-074.png)

# Mendefinisikan Objek Sendiri

Antarmuka povray Euler berisi banyak objek. Tetapi Anda tidak dibatasi untuk ini. Anda dapat membuat objek sendiri, yang menggabungkan objek lain, atau merupakan objek yang sama sekali baru.

Kami mendemonstrasikan torus. Perintah Povray untuk ini adalah "torus". Jadi kami mengembalikan string dengan perintah ini dan
parameternya. Perhatikan bahwa torus selalu berpusat pada asalnya.
 
\>function povdonat (r1,r2,look="") ...

      return "torus {"+r1+","+r2+look+"}";
    endfunction
</pre>
Here is our first torus.

\>t1=povdonat(0.8,0.2)

    torus {0.8,0.2}

Mari kita gunakan objek ini untuk membuat torus kedua, diterjemahkan dan diputar.

\>t2=povobject(t1,rotate=xrotate(90°),translate=[0.8,0,0])
 
    object { torus {0.8,0.2}
     rotate 90 *x 
     translate &lt;0.8,0,0&gt;
     }

Sekarang kami menempatkan objek ini ke dalam sebuah adegan. Untuk tampilan, kami menggunakan Phong Shading.

\>povstart(center=[0.4,0,0],angle=0°,zoom=3.8,aspect=1.5); ...  
\>   writeln(povobject(t1,povlook(green,phong=1))); ...  
\>   writeln(povobject(t2,povlook(green,phong=1))); ...  
\>   &gt; povend ();

memanggil program Povray. Namun, jika terjadi kesalahan, itu tidak menampilkan kesalahan. Karena itu Anda harus menggunakan

 &gt; povend (&lt;exit);  

jika ada yang tidak berhasil. Ini akan membuat jendela Povray terbuka.

\>povend (h=320,w=480);

    Command was not allowed!
    exec:
        return _exec(program,param,dir,print,hidden,wait);
    povray:
        exec(program,params,defaulthome);
    Try "trace errors" to inspect local variables after errors.
    povend:
        povray(file,w,h,aspect,exit); 

Berikut adalah contoh yang lebih lengkap. Kami menyelesaikannya dan menunjukkan poin yang layak dan optimal dalam plot 3D.

\>A=[10,8,4;5,6,8;6,3,2;9,5,6];

\>b=[10,10,10,10]';

\>c=[1,1,1];

Pertama, mari kita periksa, apakah contoh ini memiliki solusi.

\>x=simplex(A,b,c,\>max,\>check)'

    [0,  1,  0.5]
Yes, it has.

Next we define two objects. The first is the plane

\>function oneplane (a,b,look="") ...

      return povplane(a,b,look)
    endfunction
</pre>
Kemudian kami mendefinisikan perpotongan dari semua setengah spasi dan
sebuah kubus.

\>function adm (A, b, r, look="") ...

      ol=[];
      loop 1 to rows(A); ol=ol|oneplane(A[#],b[#]); end;
      ol=ol|povbox([0,0,0],[r,r,r]);
      return povintersection(ol,look);
    endfunction
</pre>
We can now plot the scene.

\>povstart(angle=120°,center=[0.5,0.5,0.5],zoom=3.5); ...  
\>   writeln(adm(A,b,2,povlook(green,0.4))); ...  
\>   writeAxes(0,1.3,0,1.6,0,1.5); ...  
\>  The following is a circle around the optimum.


--Terjemahan

Berikut ini adalah lingkaran di sekitar optimal.

\>writeln(povintersection([povsphere(x,0.5),povplane(c,c.x')], ...  
\>     povlook(red,0.9)));

Dan ada kesalahan di arah optimal.

\>writeln(povarrow(x,c\*0.5,povlook(red)));

Kami menambahkan teks ke layar. Teks hanyalah objek 3D. Kita perlu
menempatkan dan memutarnya sesuai dengan pandangan kita.

\>writeln(povtext("Linear Problem",[0,0.2,1.3],size=0.05,rotate=125°)); ...  
\>   povend();

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-075.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-075.png)
# Latihan Soal

1. Buatkan grafik$$f(x,y)=2^x+3y$$\>function f(x,y):= 2^x+3\*y 

\>plot3d("f"):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-077.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-077.png)

2. Buatkan grafik

$$f(x)=x^3-3x+4$

dengan a=-2, b=2, dan grid=18

\>plot3d("x^3-3\*x+4",a=-2,b=2,rotate=true,grid=18):

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-079.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-079.png)

3. Buatlah grafik plot kontur$$f(x)=e^{3xy}$$\>plot3d("exp(3\*x\*y)",angle=150°,\>contour,color=yellow):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-081.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-081.png)
4. Buat grafik plot implisit


$$x^2+y^2+5xz+3z^3$$\>plot3d("x^2+y^2+5\*x\*z+3\*z^3",\>implicit,r=2,zoom=2.2):


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-083.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-083.png)

5. Buatlah plot 3D dari fungsi
$$f(x,y)=x^3+y^2$$

dengan zoom 3 dan angle 55 derajat menggunakan povray

\>pov3d("x^3+y^2",zoom=3,angle=55°);

![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-085.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-085.png)

6. Buatlah gabungan 2 silinder dengan fungsi povx() berwarna merah dan
povz() berwarna kuning dan zoom 4

\>povstart(zoom=4)

\>c1 = povcylinder(-povx,povx,1,povlook(red));

\>c2 = povcylinder(-povz,povz,1,povlook(yellow));

\>writeln(povintersection([c1,c2]));

\>povend();


![images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-086.png](images/Alya%20Putri%20Medilasari_23030630018_EMTPlot3D-086.png)

