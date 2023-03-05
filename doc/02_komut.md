- **cmake_minimum_required(VERSION {cmake version}) :** cmake dosyasının çalışabilmesi için işletim sisteminde kullanılacak minimum cmake sürümü belirlenir. Belirtilen sürüm mevcut değilse, bir hata döndürür.

- **project(project_name LANGUAGES _ _ VERSION _) :** Cmake projesine bir isim verilir. ayrıca projede kullanılan diller ve proje versiyonu isteğe göre ayarlanabilmektedir.

- **add_executable(my_project main.cpp . . . ):** Derlenmesini istediğimiz dosyaları belirliyoruz ve ilk parametrede oluşturulacak yürütülebilir dosyanın adını belirtiyoruz.

______

- **add_library(my_add  add.cpp) :** Tüm dosyaları add_executable ile derlemek büyük projelerde sorunlara neden olabilir, bu nedenle kütüphaneleri ana dosyamızdan ayrı olarak derlemek için add_library kullanıyoruz.

- **target_link_libraries(my_project PRIVATE my_add my_print) :** add_library öğesini add_executable dosyasına bağlarız. Bu bölümde PUBLIC veya PRIVATE anahtar kelimeleri kullanılabilir. PUBLIC my_project, bu kitaplıkların onu kitaplık olarak alan diğer dosyalara aktarılmasını sağlar. PRIVATE my_project, bu kitaplıkların onu kitaplık olarak alan diğer dosyalara verilmesini engeller. PUBLIC ve PRIVATE boş bırakılırsa PUBLIC anlamına gelir.
____

- **add_subdirectory(add_dir):**  Dizinler arası geçiş sağlar. Geçerli dizindeki cmake dosyasını çalıştırır ve eski cmake dosyasına geri döner. Cmake dosyası belirtilen dizinde olmalıdır.
- **target_include_directories(my_libs PUBLIC ${PROJECT_SOURCE_DIR}/inc):**  .h dosyalarının bulunduğu dizini belirtir. PUBLIC , PRIVATE , INTERFACE gibi anahtar kelimeler kullanılabilir. PROJECT_SOURCE_DIR (proje dizini). Bu komut içerisinde birden çok PUBLIC PRIVATE kullanılabilir. `target_include_directories(my_libs PUBLIC xxx PRIVATE yyy INTERFACE zzz)`
1. PUBLIC   : Hem yürütülebilir dosyada hem de kitaplıkta kullanılıyorsa
2. PRIVATE  : Yalnızca kütüphanede kullanılıyorsa
3. INTERFACE: Kitaplıkta kullanılmıyorsa ancak yürütülebilir dosyada kullanılıyorsa
____

- **set(varvariable_name variable1 variable2 ...)**: Bir cmake değişken dizisi oluşturur. ${}, bir cmake değişkeninde bulunan değere erişmek için kullanılır.`"` işareti kullanmak zorunda değiliz. (ayrı kelimeler kullanılmayacaksa). Boşluk bir sonraki eleman anlamına gelir.
```
set(number 1 2 3)    = set(number 1;2;3)
set(name "aa;bb;cc") = set(name aa bb cc)
``` 
- **unset :** Değişkeni tanımsız yapar.
- **message():** Ekrana çıktı alınmasını sağlar. Çıkış tipi belirlenebilir.
1. message(STATUS "Cmake File Status Worked...")
2. message(DEBUG "Cmake File Debug Worked...")
3. message(WARNING "Cmake File WARNING Worked...")
4. message(FATAL ERROR "Cmake File FATAL ERROR Worked...")
5. message("Cmake File Worked...")
```
cmake dosyasını çıktı olmadan çalıştırmak için cmake -P CmakeLists.txt komutunu çalıştırın
```
___
- **list(param1, param2 ...):** Liste işlemleri için kullanılır.
1. **param1 :** Listeye ne yapılacağını belirler.
    - APPEND
    - REMOVE_AT
    - REMOVE_ITEM
    - REMOVE_DUPLICATES
    - SORT
    - INSERT
    - REVERSE
    - LENGTH
    - GET
    - SUBLIST
    - JOIN
    - FIND
2. **param2 :** Listenin adıdır. Eklenedek diğer paramatreler param1 bağlıdır.
- **string(param1 param2 ... param_out): Listenin benzeridir.
1. **param1 :** Ne yapılacağını belirler.
    - FIND
    - REPLACE
    - PREPEND
    - APPEND
    - TOLOWER
    - TOUPPER
    - LENGTH
2. **param2 :** Dizi adıdır. Eklenedek diğer paramatreler param1 bağlıdır.
3. **param_out :** Çıktıyı tutan değişkendir.
___
- **if-elseif-else-endif :** ​"1, TRUE, Y, YES, a non-zero number" doğru çıktının oluşmasını sağlar. "0, OFF, NO , FALSE, N, IGNORE, NOTFOUND, the empty string" yanlış çıktı oluşmasını sağlar.
1. DEFINED Değişkenin tanımlı olup olmadığı kontrol edilir.
2. COMMAND Komutun var olup olmadığını kontrol edin
3. EXISTS  Dosyanın belirtilen konumda olup olmadığı kontrol edilir.
 ------
- NOT
- AND
- OR
 ----
- STRLESS
- STRGREATER
- STREQUAL