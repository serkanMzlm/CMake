## CMAKE
Derleme işleminin işletim sisteminden bağımsız olarak oluşturulmasına izin veren açık kaynaklı bir sistemdir.
- **#** yorum satırı
- **"#[==[]==]"** birden fazla yorum satırı.
- Komutların büyük-küçük harf duyarlılığı yoktur. `PROJECT() - project() - ProJeCt()` komutları aynı şekilde çalışır.
```
cmake --help                              # Cmake hakkında kısa bilgi hangi build tipleri oldugunuda gösterir.
cmake --help-variable-list                # Varsayılan olarak tanımlanan değişkelerin listesini tutar.
cmake --help-variable PROJECT_BINARY_DIR  # Belirtilen değişken hakkında bilgi verir.
$ENV{}                                    # Ortam değişkenlerine erişmeyi sağlar. 
```
_____
```
# -G parametresi ile cmake build tipinin belirlenmesini sağlar.
cmake .. -G Ninja
cmake .. -G "Unix Makefiles"

# -D parametresi ile değişkenlere değer atanır. 
cmake -DCMAKE_BUILD_TYPE=Release          # Build şekli release yapıldı

# -P parametresi sayesinde çıktı almadan cmake dosyasında olan mesajları görmek için kullanılır.
cmake -P CMakeLists.txt
```
---
- cmake bir dosyayı build etmek

```
1.
mkdir build
cmake ..
make
__________________
2.
cmake -S . -B build                      # Bulunduğumuz dizini build edeceksek -S yazmaya gerek yok. -S paramtresi ile konum belirtiyoruz.
cmake --build build
__________________
3. 
cmake -B build
cd build
make
```
### Komutlar
- cmake_minimum_required
- project
- add_executable
- add_library
- add_subdirectory
- target_link_libraries
- target_include_directories
- message
- set
- list
- string
- if-elseif-else-endif
- foreach
- while
- function
- macro
- cache variable
- install
- find_package
- add_definitions
- include_directories
- option
- add_compile_options
- include
- file
- execute_process

### Makro
- PROJECT_NAME            = Project() komutunda belirtilen veriyi tutar.
- CMAKE_PROJECT_NAME      = En üst dizinde bulunan cmake dosyasında bulunan project() adı.
- CMAKE_VERSION           = Cmake versiyonunu belirtir(3.16.1)
    - CMAKE_MAJOR_VERSION 3
    - CMAKE_MINOR_VERSION 16
    - CMAKE_PATCH_VERSION 1
- CMAKE_GENERATOR          = Cmake build şeklini belirtir. (ninja makefiles...)
- CMAKE_SOURCE_DIR         = Proje dizini.
- CMAKE_CURRENT_SOURCE_DIR = Anlık bulunduğumuz dizin.
- PROJECT_SOURCE_DIR       = project() komutunun en son kullanıldığı yer.
- CMAKE_BINARY_DIR         = Projenin oluşturulduğu (build) dizini
- CMAKE_HOME_DIRECTORY     = Projde en üst dizinin yolu
- CMAKE_SYSTEM             = İşletim sisteminin tam adı.
- CMAKE_SYSTEM_NAME        = İşletim sistemi hakkında bilgi verir.(linux, windows...)
- CMAKE_INSTALL_PREFIX     = CMake tarafından yapılandırılmış bir projenin kurulum hedeflerinin nereye yerleştirileceğini belirtir.


____
```
find /usr -name <package_name>*.cmake
find /usr -name <package_name>*.pc
```

- <package_name>.pc
- <package_name>Config.cmake