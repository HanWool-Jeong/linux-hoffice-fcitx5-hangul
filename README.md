# linux-hoffice-fcitx5-hangul
리눅스 한컴오피스와 fcitx5 사용시 한글입력을 정상적으로 하기 위해 필요한 모듈입니다.<br>
[libfcitx5platforminputcontextplugin.so](https://github.com/HanWool-Jeong/linux-hoffice-fcitx5-hangul/blob/main/libfcitx5platforminputcontextplugin.so)를 다운받아서 `/opt/hnc/hoffice11/Bin/qt/plugins/platforminputcontexts`에 넣어주면 됩니다.
<br>

## 모듈 컴파일 방법
한컴오피스가 사용중인 qt 라이브러리 모듈 버전은 5.11.3입니다.<br>
<https://download.qt.io/>에 가서 5.11.3버전의 qt 인스톨러를 다운받습니다.<br>
바로다운 >> <https://download.qt.io/new_archive/qt/5.11/5.11.3/qt-opensource-linux-x64-5.11.3.run><br>
<br>

실행해줍니다.

```bash
chmod +x qt-opensource-linux-x64-5.11.3.run
./qt-opensource-linux-x64-5.11.3.run
```

실행하면 gui로 된 인스톨러가 뜨는데 필요한건 `Desktop gcc 64bit`입니다. 적당한 경로에 설치해 줍니다.<br>
컴파일 하기전, 아치리눅스 기준 `fcitx5`, `cmake`, `extra-cmake-modules` 패키지가 필요합니다.<br>
<br>

그후 [fcitx5-qt](https://github.com/fcitx/fcitx5-qt) 레포를 clone해서 설치한 qt속 gcc로 컴파일합니다.

```bash
git clone https://github.com/fcitx/fcitx5-qt.git
cd fcitx5-qt
cmake -DCMAKE_PREFIX_PATH=<방금 설치한 qt경로>/5.11.3/gcc_64 -DENABLE_QT4=0 .
cd qt5/platforminputcontext/
make -j VERBOSE=1
```
그럼 libfcitx5platforminputcontextplugin.so가 생기는데 이걸 `/opt/hnc/hoffice11/Bin/qt/plugins/platforminputcontexts`에 넣어주면 끝!!

