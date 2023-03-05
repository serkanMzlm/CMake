- **while :** Belirtilen durum doğru olduğu sürece tekrarlar.
- **foreach :** İçindeki liste elemanlarını tek tek alır ve belirtilen değişkene atar. Liste bitene kadar döngüde kalır.
```
foreach(x RANGE 10)  start
foreach(x RANGE 10 20)  start, end
foreach(x RANGE 10 20 5) start, end, increment amount
```
____
- **function(func_name , fanc_args):**  Fonksiyon içindeki global değişkenin değerini değiştirsek bile bu değer global alanda değil, sadece yerel kısımda değişir. (bu olay add_subdirectory'de geçerlidir) "PARENT_SCOPE" anahtar sözcüğü global alandaki değeri değiştirmek için kullanılır. PARENT_SCOPE, fonksiyonun içindekini değil, fonksiyonun dışındaki değişkeni değiştirir.

1. ARGC
2. ARGV
3. ARGN
4. ARG_number
- **macro(func_name , fanc_args):** fonksiyon ile her şey aynı sayılır, fonksiyonlar bir makroya dönüştürülürse kod hatasız çalışır. Aralarındaki fark, makro fonksiyonun içinde global bir değişken değeri değiştiğinde, bunun doğrudan etkisinin dışarıdaki değişken üzerinde olmasıdır. (PARENT_SCOPE kullanmaya gerek yok)
____
- **cache variable :** Bir değişkeni önbellek değişkeni olarak tanımlamak, o değişkenin değerinin her seferinde yeniden hesaplanmamasını sağlar. Bu özellik, projenin oluşturma sürecinin her seferinde tekrar eden ve zaman alan süreçlerini optimize etmeye yardımcı olabilir.
1. Bu sayede inşaat sürecinde tekrar eden süreçler en aza indirilmekte ve hızlandırılmaktadır.
2. Build klasöründe bulunan CMakeCache.txt dosyasına kaydedilir.
3. Belirttiğimiz değişkeni başka bir yerde ayarlasak bile önbellek değişmez, sabit kalır. "FORCE" veya build sırasında `cmake -Dvariable` değiştirilebilir.
- **ENV :** Bir ortam değişkenine erişmek, onu değiştirmek vb. istiyorsak kullanılır.
___
- **install() :** Asıl amacı belirtilen dosyayı istenilen yere kopyalamaktır. İsteğe göre kütüphaneleri /usr/local içindeki belirli bölümlere kopyalayıp diğer projelerimizde çalışmasını sağlıyoruz. "sudo make install" olmadan cmake'de belirttiğimiz install komutu çalışmayacaktır. Bu örnekte sudo kullanmamızın nedeni kurulumu yapacağımız yerin izin istemesidir.
1. FILES dosyayı kopyalar
2. TARGETS dizin kopyaları
3. EXPORT Yaptığımız dosyaları find_package komutu ile bulabilmemiz için gerekli forma dönüştürür.

```
make sudo make install 
```
Header Files: /usr/local/include/<package_name>

Targets: /usr/local/lib/<package_name>
___
- **find_package(ABC) :** ABC-config.cmake'i arar, aradığı klasör /usr/local/lib/ABC'dir.
1. REQUIRED ile bu dosyaya sahip olmayı zorunlu hale getiriyoruz.
2. MODULE Modül olarak arama yapmak için kullanılır find_package(my_lib MODULE) -> Findmy_lib.cmake
3. CONFIG Bir yapılandırma olarak arama yapmak için kullanılır find_package(my_lib MODULE) -> my_lib-config.cmake
**Not :** Belirtilmemişse, önce MODULE modunda arar, ardından CONFIG modunda arar.
___
- **add_definitions() :** Derleme zamanında kullanılan tanımları eklemek için kullanılır. Ayrıca doğrudan sistemde kullanabileceğimiz makroları tanımlamamızı sağlayabilir. -D parametresi sisteme yeni bir makro eklemek için kullanılır.
___
- **target_include_directories(my_libs PUBLIC ${PROJECT_SOURCE_DIR}/inc):**  .h dosyalarının bulunduğu dizini belirtir. PUBLIC , PRIVATE , INTERFACE gibi anahtar kelimeler kullanılabilir. PROJECT_SOURCE_DIR (proje dizini). Bu komut içerisinde birden çok PUBLIC PRIVATE kullanılabilir. `target_include_directories(my_libs PUBLIC xxx PRIVATE yyy INTERFACE zzz)`
1. PUBLIC   : Hem yürütülebilir dosyada hem de kitaplıkta kullanılıyorsa
2. PRIVATE  : Yalnızca kütüphanede kullanılıyorsa
3. INTERFACE: Kitaplıkta kullanılmıyorsa ancak yürütülebilir dosyada kullanılıyorsa
- **include_directories :** Proje kitaplıklarının konumunu gösterir. target_include_directories komutu ile arasında ki farklar
1. "include_directories" işlevi, verilen dizinleri projenin tüm hedefleri için geçerli kılar. Bu, projenin tüm kaynak dosyalarının verilen dizinleri içeren başlık dosyalarını bulmasını sağlayacaktır.
2. "target_include_directories" işlevi, verilen dizinleri yalnızca belirli bir hedef için geçerli kılar. Bu, yalnızca belirtilen hedef tarafından kullanılan başlığı bulmasını sağlar ve diğer hedefin verilen dizinleri kullanmasını engeller.
___
- **option :** CMake yapılandırma işlemi sırasında kullanıcıya bir seçenek sunmanıza olanak tanır. Seçenek, CMake dosyalarında bir değişken olarak tanımlanır ve değer, komut satırından veya CMake GUI aracından belirtilir. 
```
cmake -DENABLE_FEATURE=ON ..
```
- **add_compile_options :** Derleme zamanında ekstra parametreler eklememizi sağlar
1. -w  Tüm uyarı mesajlarını engeller
2. -Werror Tüm uyarıları hataya çevirir
3. -Wall  tüm uyarıları gösterir
4. -Wextra Ayrıntılı uyarılar gösterir.
```
add_compile_options(-w)
add_compile_options(-std=c++11)
```
___
- **include :** Sisteme başka bir cmake dosyası eklememizi sağlar.
```
include(${CMAKE_BINARY_DIR}/conanbuildinfo.cmake)
include(src/CMakeLists.txt)
```
- **file :**  Dosya okuma yazma vb. işlemler için kullanılır.
1. GLOB  geçerli dizindeki dosyaların listesini almak için.
2. GLOB_RECURSE geçerli dizindeki ve tüm alt dizinlerindeki dosyaların bir listesini almak için.
```
file(GLOB_RECURSE myfiles  ${PROJECT_SOURCE_DIR}/src/*.cpp ${PROJECT_SOURCE_DIR}/inc/*.h)
```
- **execute_process :**  Terminalde komutu çalıştırır. Örneğin, uygulama her çalıştığında github'dan önce kodu çekmesini isteyebiliriz.
1. COMMAND çalıştırılacak komutu ifade edin
2. WORKING_DIRECTORY komutların çalışacağı dizini ifade eder.
3. RESULT_VARIABLE komutun sonucu başarılı olursa 0, başarısız olursa 1 döndürür.
4. OUTPUT_VARIABLE komut çıktısını tutar.
5. ERROR_VARIABLE Komutta bir hata varsa bu hatayı korur.
