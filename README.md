---
icon: '1'
cover: >-
  https://images.unsplash.com/photo-1658989044880-2871105f4ec6?crop=entropy&cs=srgb&fm=jpg&ixid=M3wxOTcwMjR8MHwxfHNlYXJjaHw0fHxob2xvZ3JhbXxlbnwwfHx8fDE3MjUzNzkzNTB8MA&ixlib=rb-4.0.3&q=85
coverY: 0
layout:
  cover:
    visible: true
    size: full
  title:
    visible: true
  description:
    visible: true
  tableOfContents:
    visible: true
  outline:
    visible: true
  pagination:
    visible: true
---

# Virtualization

## Apa itu virtual?

Virtual memiliki arti sesuatu yang tidak nyata.&#x20;

Sedangkan dalam teknologi komputer, virtual artinya teknologi yang bisa kita gunakan untuk membuat sumber daya komputer(server, storage, network, dan hardware lainnya) menjadi virtual/tidak berwujud nyata.&#x20;

Dengan virtualisasi memungkinkan untuk membagikan sumber daya komputer secara virtual dan bisa menjalankan beberapa virtual mesin secara bersama diatas hardwarenya.&#x20;

Hardaware fisik yang menjalankan software virtualisasi(hypervisor) disebut <mark style="color:orange;">**host**</mark> dan virtual mesin yang diinstal di atas hypervisor disebut <mark style="color:orange;">**guest**</mark>. Beberapa teknologi software yang bisa digunakan untuk memulai virtualisasi adalah KVM, Xen, QEMU, dan VirtualBox.&#x20;

<figure><img src=".gitbook/assets/Grafana (1).png" alt=""><figcaption></figcaption></figure>

***

## Apa keuntungannya?

1. Mengurangi fisik atau bare metal server, mengurangi komponen jaringan, dan mengurangi komponen fisik lainnya(rak), mengurangi pengeluaran uang, dan bisa meningkatkan utilisasi hardware yang kita miliki.
2. Mengisolasi aplikasi dan menghilangkan masalah kompatibilitas aplikasi dengan menyediakan banyak virtual mesin.
3. Bisa menyediakan virtual mesin dengan cepat, baik dari image ataupun snapshot.
4. Pemulihan yang cepat. Jika terjadi suatu masalah pada virtual mesin, kita bisa mengambil snapshot dari virtual mesin dan membuat ulang virtual mesin.&#x20;
5. Memiliki fleksibilitas dalam memindahkan virtual mesin ke data center yang baru, contohnya pada openstack ada teknik _<mark style="color:orange;">**migration**</mark>_.

**Referensi:**&#x20;

{% embed url="https://www.ibm.com/think/insights/virtualization-benefits#5+benefits+of+virtualization" %}

***

## Tipe virtualization

#### **1. Desktop virtualization** (**Virtual Desktop Infrastructure**)

<figure><img src=".gitbook/assets/Grafana (2).png" alt=""><figcaption></figcaption></figure>

[**Desktop virtualization**](https://www.intel.com/content/www/us/en/business/enterprise-computers/resources/virtual-desktop-infrastructure.html) merujuk pada metode yang memisahan sesi desktop dengan pengguna yang mengaksesnya(akses jarak jauh). Sesi desktop dihosting dan divirtualisasi secara terpusat pada server. Desktop virtual kemudian dibuat mudah diakses oleh pengguna melalui perangkat yang tersedia(PC, Laptop, HP).&#x20;

#### **2. Server virtualization**

<figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20200813134720/servervirtualizationcloudcomputing.png" alt=""><figcaption></figcaption></figure>

[**Server virtualization**](https://www.geeksforgeeks.org/server-virtualization/) adalah metode membagi-bagi sebuah fisik server menjadi beberapa virtual mesin yang berjalan dengan OSnya sendiri secara independen. Untuk menerapkan server virtualization, kita perlu menginstall hypervisor pada fisik server. Hypervisor digunakan untuk mengelola dan mengalokasi sumber daya yang ada pada fisik server ke setiap virtual mesin.

#### **3. Application virtualization**

<figure><img src=".gitbook/assets/Grafana (3).png" alt=""><figcaption></figcaption></figure>

[**Ini**](https://www.wallarm.com/what/what-is-application-virtualization-by-wallarm) adalah sebuah cara untuk mengakses aplikasi tanpa perlu mendownload dan menginstallnya. Jadi, aplikasi akan dideploy pada server, lalu user bisa mengakses dan menggunakannya seolah-olah aplikasi berjalan secara langsung pada perangkat mereka. Ini sangat bermanfaat karena bisa mendukung penggunaan aplikasi pada selain OS yang dirancang untuk aplikasinya.

#### **4. Network virtualization**

<figure><img src=".gitbook/assets/Grafana (4).png" alt=""><figcaption></figcaption></figure>

[**Network virtualization**](https://www.netmaker.io/resources/network-virtualization) adalah konsep mengubah jaringan yang awalnya berbasis hardware menjadi berbasis software. Virtualisasi ini memanfaatkan hardware jaringan seperti router, switch, firewall dan mengubahnya menjadi software. Sehingga pengguna mudah untuk mengelola dan mengontrol jaringannya melalui software. Tanpa virtualisasi, bisa jadi kita memerlukan banyak hardaware jaringan untuk dipasang terpisah pada server. Oleh karena itu **Network virtualization** membuat pengelolaan jaringan menjadi lebih sederhana dan fleksibel.  &#x20;

#### **5. Storage virtualization**

<figure><img src=".gitbook/assets/Grafana (5).png" alt=""><figcaption></figcaption></figure>

[**Storage virtualization**](https://www.storagetutorials.com/what-storage-virtualization/) adalah teknik mengumpulkan storage hardware seperti hdd, ssd, atau nvme menjadi satu penyimpanan virtual(logical storage). Penyimpanan virtual ini bisa ditugaskan ke VM untuk digunakan. Untuk contoh dari storage virtualization adalah LUN’s(Logical unit number), Logical volume(LV), [RAID groups](https://www.storagetutorials.com/raid-5-vs-raid-6/), dll. Keuntungannya kita bisa menyediakan penyimpanan besar untuk menangani kebutuhan penyimpanan data yang meningkat.

***

## Protection ring

<figure><img src="https://www.tutorialspoint.com/assets/questions/media/629838-1700653312.jpg" alt=""><figcaption></figcaption></figure>

Didalam komputer yang kita jalankan terdapat sebuah mekanisme yang mengatur hak istimewa pada setiap lapisannya, mekanisme ini disebut [**Protection Ring**](https://www.tutorialspoint.com/protection-ring). [**Protection Ring**](https://www.tutorialspoint.com/protection-ring) disusun dari beberapa urutan lapisan tingkatan hak istimewa dari yang paling tinggi sampai yang paling rendah.&#x20;

Hardware yang memiliki CPU dengan arsitektur x86 memiliki 4 lapisan, dari Ring 0 sampai Ring 3. dimana Ring 0 memiliki hak istimewa paling tinggi dan digunakan oleh OS untuk mengatur dan mengelola hardware, sedangkan **Ring 3** digunakan oleh pengguna aplikasi dengan hak istimewa yang rendah sehingga terbatas untuk mengakses sumber daya hardwarenya.

### Apa Keuntungannya?&#x20;

1. **Dapat meningkatkan keamanan sistem operasi**\
   Ketika suatu proses membutuhkan instruksi yang memerlukan sumber daya CPU(seperti cache, thread, core, instruction set, dll), proses tersebut akan mengirimkan request dan meminta persetujuan dari sistem operasi. Sistem operasi akan menentukan apakah proses tersebut layak diberikan hak akses istimewa atau tidak. Dengan demikian, sistem operasi dapat mengontrol akses dan mencegah proses berbahaya atau serangan eksternal untuk mengakses sumber daya yang sensitif.
2. **Toleransi terhadap kesalahan(fault tolerance)**\
   [Crash](https://www.bobology.com/public/What-is-a-Computer-Crash.cfm) pada sistem(program gagal dan berheti bekerja) dapat dikurangi dengan memberikan toleransi kesalahan(fault tolerance) kepada aplikasi ataupun program yang memiliki akses langsung ke ruang kernel di Ring 0. Sehingga semisal terdapat crash, Ring 0 akan memberikan toleransi untuk mencegah terjadinya crash di seluruh sistem. Jadi, sistem tetap berfungsi normal. &#x20;

### Level Protection Ring

* **Ring 0**\
  [Kernel](https://www.javatpoint.com/what-is-kernel) adalah program yang menjadi inti pada OS, bisa diibaratkan kernel itu seperti jantung dari OS. Karena kernel berada pada Ring 0, kernel dapat mengakses seluruh sumber daya sistem(CPU dan memori) . Proses yang berjalan pada Ring 0 disebut proses mode kernel. Proses pada mode kernel memiliki hak istimewa yang tinggi, sehingga dapat memengaruhi seluruh sistem. &#x20;
* **Ring 1**\
  Biasanya OS memanfaatkan Ring 1 untuk berinteraksi dengan hardware komputer. Interaksi dengan hardware ini akan menjalankan instruksi proses, contohnya kita ingin melakukan streaming/mengambil video dengan kamera laptop dan mengetik pada keyboard laptop.
* **Ring 2**\
  Ring 2 berfungsi untuk mengeksekusi perintah yang berkaitan dengan sistem penyimpanan, pemuatan data, dan menyimpan data. Misalnya ketika OS perlu mengelola data di penyimpanan, seperti membaca atau menulis file dari disk, operasi ini akan dilakukan pada Ring 2.
* **Ring 3**\
  User dapat menjalankan sebuah proses pada Ring 3(hak istimewa rendah). Ketika proses user membutuhkan sumber daya, maka proses tersebut akan diteruskan ke kernel pada Ring 0, tujuannya agar proses tersbut dapat mengakses sumber daya untuk aplikasi yang dibutuhkan. Aplikasi seperti web browser, editor teks, dan game berjalan pada Ring 3.

### Interaksi pada Privilege Rings

* **Supervisor Mode**\
  [Supervisor mode/privilege mode](https://www.tutorialspoint.com/supervisor-mode-privileged-mode) adalah mode yang akan mengeksekusi semua jenis instruksi, termasuk juga privileged instructions. Mode ini digunakan prosesor untuk menjalankan tugas seperti penjadwalan proses, pengelolaan memori, instruksi interupsi, manajemen input dan output untuk menjaga stabilitas dan keamanan sistem. Biasanya, OS berjalan pada mode ini karena membutuhkan akses kontrol penuh atas sumber daya hardware.
* **Hypervisor Mode**\
  [Mode ini](https://www.geeksforgeeks.org/protection-ring/) didukung oleh versi CPU terbaru, dengan menyediakan fitur virtualisasi untuk arsitektur x86. Guest OS menggunakan mode hypervisor untuk mengontrol akses sumber daya pada hardware(Ring 0). Intel VT-x dan AMD-v membuat lapisan baru yaitu Ring -1. Ring baru ini(Ring -1) dimaksudkan untuk digunakan oleh hypervisor.

**Sumber:**

{% embed url="https://www.geeksforgeeks.org/protection-ring/" %}

{% embed url="https://www.tutorialspoint.com/protection-ring" %}

{% embed url="https://www.baeldung.com/cs/os-rings" %}

***

## Tipe Virtualisasi Server

### **Full virtualization**

<figure><img src="https://static.packt-cdn.com/products/9781784399054/graphics/3990_01_04.jpg" alt=""><figcaption></figcaption></figure>

[**Full virtualization**](https://www.sciencedirect.com/topics/computer-science/full-virtualization) adalah tipe virtualisasi server yang menyediakan Guest OS dan sepenuhnya meniru hardware fisiknya. Guest OS disediakan tanpa memerlukan modifikasi dan sepenuhnya terisolasi. Full virtualization memiliki 2 jenis, yaitu:

#### 1. Full Virtualization dengan Binary Translation dan **Direct Execution (Software-based)** <a href="#id-3f6c" id="id-3f6c"></a>

<figure><img src=".gitbook/assets/Grafana (8).png" alt=""><figcaption></figcaption></figure>

[**Dengan pendekatan ini**](https://mohitdtumce.medium.com/understanding-full-virtualization-paravirtualization-and-hardware-assist-730d3c9aa04c), OS apapun bisa divirtualisasikan dengan menggunakan teknik Binary Translation dan Direct Execution.&#x20;

* Bagaimana penerapan **Binary Translation**?\
  Jadi pada kernel Guest OS, terdapat instruksi yang tidak dapat dijalankan secara langsung pada lingkungan virtual_<mark style="color:yellow;">(non virtualizable instructions)</mark>_. Oleh karena itu, hypervisor menerjemahkan instruksi tersebut dengan menggantinya menjadi urutan instruksi baru yang bisa berjalan pada lingkungan virtual. Sehingga kita tidak perlu melakukan modifikasi pada Guest OS.
* Penerapan **Direct Execution**\
  Untuk instruksi yang dijalankan di tingkat pengguna_<mark style="color:yellow;">(user level code)</mark>_, instruksi tersebut tidak memerlukan modifikasi dan bisa dieksekusi secara langsung oleh hardware(tepatnya di CPU fisik). Sehingga Guest OS dapat memberikan kinerja yang lebih baik untuk aplikasi yang berjalan di dalam mesin virtual, menjadikannya lebih efisien dan optimal.

> **Kesimpulan:**&#x20;
>
> Hypervisor menerjemahkan semua instruksi Guest OS menjadi instruksi yang bisa berjalan pada lingkungan virtual dan bisa menyimpan hasilnya untuk digunakan di masa mendatang, sementara itu instruksi tingkat pengguna dapat berjalan tanpa modifikasi dan dieksekusi dengan cepat.

#### 2. Full Virtualization dengan bantuan Hardware <a href="#id-1a26" id="id-1a26"></a>

<figure><img src="https://learning.oreilly.com/api/v2/epubs/urn:orm:book:9781788299558/files/assets/eb74f0c8-ac76-4a61-b642-8de0749b105c.png" alt=""><figcaption></figcaption></figure>

Intel dan AMD menyelesaikan tantangan virtualisasi pada full virtualization dan paravirtualization yang berjalan di arsitektur x86. Dengan membuat ekstensi baru untuk prosesor yang disebut Intel VT-x(**Virtualization Technology(VT)**) dan AMD-V(**Secure Virtual Machine(SVM)**).&#x20;

Ekstensi ini membuat hypervisor mengizinkan guest OS untuk berjalan pada mode kernel atau di dalam Ring 0. Hal ini berpengaruh pada guest OS karena memiliki instruksi istimewa dan bisa melakukan panggilan sensitif yang otomatis [terperangkap(trap)](https://developer.arm.com/documentation/102142/0100/Trapping-and-emulation-of-instructions) oleh Hypervisor dan tidak perlu diterjemahkan lagi, sehingga guest OS memiliki akses langsung ke sumber daya hardware tanpa emulasi/meniru dan tanpa modifikasi OS.

Pada virtualisasi ini, hypervisor beroperasi pada mode root baru di dalam Ring -1 (memiliki tingkat istimewa yang lebih tinggi dari Ring 0). Dengan hypervisor bekerja di dalam **Ring -1**, mesin virtual (VM) yang berjalan pada **Ring 0** seolah-olah memiliki hak akses penuh, tetapi hypervisor tetap dapat **mengisolasi VM satu sama lain** dan dari sistem host. Karena ini juga akan mengurangi overhead di hypervisor.

**Referensi:**&#x20;

{% embed url="https://learning.oreilly.com/library/view/enterprise-cloud-security/9781788299558/ee606769-4300-4d69-84f6-5ec8226490ea.xhtml" %}

{% embed url="https://mohitdtumce.medium.com/understanding-full-virtualization-paravirtualization-and-hardware-assist-730d3c9aa04c" %}

### Paravirtualization

<figure><img src="https://media.geeksforgeeks.org/wp-content/uploads/20200519134631/Paravirtualization.png" alt=""><figcaption></figcaption></figure>

[**Paravirtualization**](https://www.serverwatch.com/virtualization/what-is-paravirtualization/) adalah tipe virtualisasi server yang melakukan modifikasi pada guest OS-nya. Guest OS tahu bahwa ia berjalan di lingkungan virtual di atas hypervisor(tidak secara langsung di atas hardwarenya). **Paravirtualization** bekerja menggunakan teknik [<mark style="color:orange;">**hypercall**</mark>](https://learn.microsoft.com/en-us/virtualization/hyper-v-on-windows/tlfs/hypercall-interface), artinya guest OS bisa berkomunikasi secara langsung dengan hypervisor. Jadi guest OS akan mengirimkan instruksi melalui panggilan system dan secara langsung dikirim ke hypervisor tanpa melakukan penerjemahan binary(Binary Translation).&#x20;

<figure><img src="https://lh6.googleusercontent.com/iCsltY0qT-uSUoGDxMflL5V7Rhgs5EcKi2SPlEIy5i1e3ai327HOYfFdyyMBwCvZftREUFQN5cDkDdadq4uk7EyNBfUw5ZUfVhWegdh38uNrz2BxNX6XVZA3dMsBhc6xSJbB4Z0u" alt=""><figcaption></figcaption></figure>

Keuntungan menggunakan hypercall adalah instruksi dari guest OS lebih cepat dan mudah dieksekusi oleh hypervisor. Konsepnya seperti kita bisa berbahasa Inggris dengan lancar, jadi ketika sedang liburan di Inggris kita mudah dan lancar berkomunikasi dengan orang lain di sana.

Guest OS pada **paravirtualization** juga tidak sepenuhnya terisolasi, karena mereka berbagi sumber daya dan dapat dimodifikasi penggunaannya sesuai dengan kebutuhan. Pendekatan ini memungkinkan guest OS untuk meningkatkan(scale up) atau menurunkan(scale down) sumber daya yang digunakannya secara fleksibel.

**Referensi:**

{% embed url="https://techslang.com/definition/what-is-paravirtualization/" %}

{% embed url="https://www.serverwatch.com/virtualization/what-is-paravirtualization/" %}

