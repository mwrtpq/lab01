1. Скачайте библиотеку boost с помощью утилиты wget.

```bash
wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
```

```bash
 wget https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
--2026-04-01 11:59:46--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz
Resolving sourceforge.net (sourceforge.net)... 104.18.13.149, 104.18.12.149, 2606:4700::6812:d95, ...
Connecting to sourceforge.net (sourceforge.net)|104.18.13.149|:443... connected.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/ [following]
--2026-04-01 11:59:46--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/
Reusing existing connection to sourceforge.net:443.
HTTP request sent, awaiting response... 301 Moved Permanently
Location: https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download [following]
--2026-04-01 11:59:47--  https://sourceforge.net/projects/boost/files/boost/1.69.0/boost_1_69_0.tar.gz/download
Reusing existing connection to sourceforge.net:443.
HTTP request sent, awaiting response... 302 Found
Location: https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABpzN6DiW65gLTx-fAtMxa0kYYvP4RoOMql6oGiwraVtR8Bz-LUEBmcXwKBtSPa9H2Flniqm6jXMjAbPtWwxf0o9jKfJw%3D%3D&use_mirror=deac-riga&r= [following]
--2026-04-01 11:59:47--  https://downloads.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?ts=gAAAAABpzN6DiW65gLTx-fAtMxa0kYYvP4RoOMql6oGiwraVtR8Bz-LUEBmcXwKBtSPa9H2Flniqm6jXMjAbPtWwxf0o9jKfJw%3D%3D&use_mirror=deac-riga&r=
Resolving downloads.sourceforge.net (downloads.sourceforge.net)... 104.18.13.149, 104.18.12.149, 2606:4700::6812:c95, ...
Connecting to downloads.sourceforge.net (downloads.sourceforge.net)|104.18.13.149|:443... connected.
HTTP request sent, awaiting response... 302 Found
Location: https://deac-riga.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1 [following]
--2026-04-01 11:59:48--  https://deac-riga.dl.sourceforge.net/project/boost/boost/1.69.0/boost_1_69_0.tar.gz?viasf=1
Resolving deac-riga.dl.sourceforge.net (deac-riga.dl.sourceforge.net)... 89.111.52.100
Connecting to deac-riga.dl.sourceforge.net (deac-riga.dl.sourceforge.net)|89.111.52.100|:443... connected.
HTTP request sent, awaiting response... 200 OK
Length: 111710205 (107M) [application/x-gzip]
Saving to: ‘boost_1_69_0.tar.gz.2’

boost_1_69_0.tar.gz.2         100%[=================================================>] 106.53M  1.86MB/s    in 1m 40s

2026-04-01 12:01:29 (1.06 MB/s) - ‘boost_1_69_0.tar.gz.2’ saved [111710205/111710205]
```

2. Разархивируйте скаченный файл в директорию ~/boost_1_69_0

```bash
tar -xzf boost_1_69_0.tar.gz
```

3. Подсчитайте количество файлов в директории ~/boost_1_69_0 не включая вложенные директории.

```bash
find ~/boost_1_69_0 -maxdepth 1 -type f | wc -l
```
```
17
```

4. Подсчитайте количество файлов в директории ~/boost_1_69_0 включая вложенные директории.

```bash
find ~/boost_1_69_0 -type f | wc -l
```
```
62117
```
5. Подсчитайте количество заголовочных файлов, файлов с расширением .cpp, сколько остальных файлов.

```bash
find ~/boost_1_69_0 -type f -name "*.hpp" | wc -l
```
```
14912
```

```bash
find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l
```
```
13789
```

```bash
echo $(( $(find ~/boost_1_69_0 -type f | wc -l) - $(find ~/boost_1_69_0 -type f -name "*.hpp" | wc -l) - $(find ~/boost_1_69_0 -type f -name "*.cpp" | wc -l) ))
```
```
33416
```

6. Найдите полный пусть до файла any.hpp внутри библиотеки boost.

```bash
find ~/boost_1_69_0 -name "any.hpp"
```
```
/home/a/boost_1_69_0/boost/hana/fwd/any.hpp
/home/a/boost_1_69_0/boost/hana/any.hpp
/home/a/boost_1_69_0/boost/proto/detail/any.hpp
/home/a/boost_1_69_0/boost/fusion/algorithm/query/detail/any.hpp
/home/a/boost_1_69_0/boost/fusion/algorithm/query/any.hpp
/home/a/boost_1_69_0/boost/fusion/include/any.hpp
/home/a/boost_1_69_0/boost/xpressive/detail/utility/any.hpp
/home/a/boost_1_69_0/boost/type_erasure/any.hpp
/home/a/boost_1_69_0/boost/any.hpp
/home/a/boost_1_69_0/boost/spirit/home/support/algorithm/any.hpp
```

7. Выведите в консоль все файлы, где упоминается последовательность boost::asio.

```bash
grep -R -l "boost::asio" ~/boost_1_69_0 > task7.txt
```

8. Скомпилирутйе boost.

```bash
cd ~/boost_1_69_0
```

```bash
./bootstrap.sh
```

```bash 
Building Boost.Build engine with toolset gcc... tools/build/src/engine/bin.linuxx86_64/b2
Unicode/ICU support for Boost.Regex?... not found.
Backing up existing Boost.Build configuration in project-config.jam.1
Generating Boost.Build configuration in project-config.jam...

Bootstrapping is done. To build, run:

    ./b2 > task8.txt

```

9. Перенесите все скомпилированные на предыдущем шаге статические библиотеки в директорию ~/boost-libs.

```bash
mkdir -p ~/boost-libs
```

```bash
find . -name "*.a" -exec cp {} ~/boost-libs \;
```

10. Подсчитайте сколько занимает дискового пространства каждый файл в этой директории.

```bash
du -h ~/boost-libs/*
```
```
4.0K    /home/a/boost-libs/libboost_atomic.a
236K    /home/a/boost-libs/libboost_chrono.a
148K    /home/a/boost-libs/libboost_container.a
24K     /home/a/boost-libs/libboost_context.a
332K    /home/a/boost-libs/libboost_contract.a
152K    /home/a/boost-libs/libboost_date_time.a
4.0K    /home/a/boost-libs/libboost_exception.a
232K    /home/a/boost-libs/libboost_fiber.a
416K    /home/a/boost-libs/libboost_filesystem.a
848K    /home/a/boost-libs/libboost_graph.a
172K    /home/a/boost-libs/libboost_iostreams.a
2.0M    /home/a/boost-libs/libboost_locale.a
544K    /home/a/boost-libs/libboost_math_c99.a
448K    /home/a/boost-libs/libboost_math_c99f.a
464K    /home/a/boost-libs/libboost_math_c99l.a
2.7M    /home/a/boost-libs/libboost_math_tr1.a
2.6M    /home/a/boost-libs/libboost_math_tr1f.a
2.7M    /home/a/boost-libs/libboost_math_tr1l.a
212K    /home/a/boost-libs/libboost_prg_exec_monitor.a
1.6M    /home/a/boost-libs/libboost_program_options.a
80K     /home/a/boost-libs/libboost_random.a
2.7M    /home/a/boost-libs/libboost_regex.a
1.2M    /home/a/boost-libs/libboost_serialization.a
24K     /home/a/boost-libs/libboost_stacktrace_addr2line.a
20K     /home/a/boost-libs/libboost_stacktrace_backtrace.a
16K     /home/a/boost-libs/libboost_stacktrace_basic.a
4.0K    /home/a/boost-libs/libboost_stacktrace_noop.a
4.0K    /home/a/boost-libs/libboost_system.a
2.3M    /home/a/boost-libs/libboost_test_exec_monitor.a
56K     /home/a/boost-libs/libboost_timer.a
2.3M    /home/a/boost-libs/libboost_unit_test_framework.a
4.5M    /home/a/boost-libs/libboost_wave.a
796K    /home/a/boost-libs/libboost_wserialization.a
```

11. Найдите топ10 самых "тяжёлых".

```bash
du -h ~/boost-libs/* | sort -hr | head -10
```

```
4.5M    /home/a/boost-libs/libboost_wave.a
2.7M    /home/a/boost-libs/libboost_regex.a
2.7M    /home/a/boost-libs/libboost_math_tr1l.a
2.7M    /home/a/boost-libs/libboost_math_tr1.a
2.6M    /home/a/boost-libs/libboost_math_tr1f.a
2.3M    /home/a/boost-libs/libboost_unit_test_framework.a
2.3M    /home/a/boost-libs/libboost_test_exec_monitor.a
2.0M    /home/a/boost-libs/libboost_locale.a
1.6M    /home/a/boost-libs/libboost_program_options.a
1.2M    /home/a/boost-libs/libboost_serialization.a
```
