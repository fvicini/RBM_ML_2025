# Colab Users Instructions

```bash
%cd /content
!git clone https://github.com/fvicini/CppToPython.git
%cd CppToPython/
```

```bash
!git submodule init
!git submodule update
```

```bash
!mkdir externals
%cd externals/
!cmake -DINSTALL_VTK=OFF -DINSTALL_LAPACK=OFF ../gedim/3rd_party_libraries
!make -j4
%cd ..
```

```bash
!mkdir release
%cd release
!cmake -DCMAKE_PREFIX_PATH="/content/CppToPython/externals/Main_Install/eigen3;/content/CppToPython/externals/Main_Install/triangle;/content/CppToPython/externals/Main_Install/tetgen;/content/CppToPython/externals/Main_Install/googletest;/content/CppToPython/externals/Main_Install/lapack" -DENABLE_TRIANGLE=ON -DENABLE_TETGEN=ON ../
!make -j4 GeDiM4Py
%cd /content/
```