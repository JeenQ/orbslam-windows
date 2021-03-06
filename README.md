# ORB_SLAM2_Windows

2020 winter Handong Global University advanced computer vision camp

Easy build for ORB Slam 2 on Windows

## 1. Make a directory called build in orbslam-windows/Thirdparty/DBoW2
- Run CMake GUI and set source code to orbslam-windows/Thirdparty/DBoW2 and where to build the binaries to orbslam-windows/Thirdparty/DBoW2/build
- Press Configure and choose Visual Studio 14 2015 Win64 or Visual Studio 12 2013 Win64
- OpenCV_DIR : "C:\opencv\build" or "C:\opencv\build\x64\vc15\lib"
- Press Generate
- Open the resulting project in the build directory in Visual Studio
- Change build type to Release (in white box up top, should initially say Debug)
- Right click on DBoW2 project -> Properties -> 일반 : Configuration Type to Static Library (.lib), 고급: change Target Extension to .lib 
- Go to C/C++ Tab -> Code Generation and change Runtime Library to Multi-threaded (/MT)
- Build ALL_BUILD. You should get lots of warnings but no errors

## 2. Make a directory called build in orbslam-windows/Thirdparty/g2o
- Run CMake GUI and set source code to orbslam-windows/Thirdparty/g2o and where to build the binaries to orbslam-windows/Thirdparty/g2o/build
- Press Configure and choose Visual Studio 14 2015 Win64 or Visual Studio 12 2013 Win64
- Press Generate
- Open the resulting project in the build directory in Visual Studio
- Change build type to Release (in white box up top, should initially say Debug)
- Right click on g2o project -> Properties -> 일반 : Configuration Type to Static Library (.lib), 고급: change Target Extension to .lib 
- Go to C/C++ Tab -> Code Generation and change Runtime Library to Multi-threaded (/MT)
- Go to C/C++ -> Preprocessor and press the dropdown arrow in the Preprocessor Definitions, then add a new line with WINDOWS on it (no underscore), then press OK, then Apply
- Build ALL_BUILD.

## 3. Make a directory called build in orbslam-windows/Thirdparty/Pangolin
- Run CMake GUI and set source code to orbslam-windows/Thirdparty/Pangolin and where to build the binaries to orbslam-windows/Thirdparty/Pangolin/build
- Press Configure and choose Visual Studio 14 2015 Win64 or Visual Studio 12 2013 Win64. You'll have a lot of RED and a lot of things that say DIR-NOTFOUND but as long as the window at the bottom says Configuring Done you're fine
- Press Generate
- Open the resulting project in the build directory in Visual Studio
- Change build type to Release (in white box up top, should initially say Debug)
- Build ALL_BUILD. You'll have an error by project testlog that says "cannot open input file 'pthread.lib'" but that doesn't matter cause we don't use testlog. Everything else should build fine, i.e., you should have
========== Build: 18 succeeded, 1 failed, 0 up-to-date, 0 skipped ==========

## 4. Make a directory called build in orbslam-windows
- Run CMake GUI and set source code to orbslam-windows and where to build the binaries to orbslam-windows/build
- Press Configure and choose Visual Studio 14 2015 Win64 or Visual Studio 12 2013 Win64
- OpenCV_DIR : "C:\opencv\build" or "C:\opencv\build\x64\vc15\lib"
- Press Generate
- Open the resulting project in the build directory in Visual Studio
- Change build type to Release (in white box up top, should initially say Debug)
- Right click on ORB_SLAM2 project -> Properties -> 일반 : Configuration Type to Static Library (.lib), 고급: change Target Extension to .lib 
- Go to C/C++ Tab -> Code Generation and change Runtime Library to Multi-threaded (/MT)

I had to disable warnings in Orb Slam because otherwise there were so many they crashed visual studio. You will still see a few but not very many

- Right click on the ORB_SLAM2 project (NOT ALL_BUILD) and click Build
- If you're lucky, that will take few minutes then successfully build!

## 5. mono_kitti
- Right click on that project and go to Properties -> C/C++ -> Code Generation, and change Runtime Library to Multi-threaded (/MT). Then press apply
- Right click on it and press build
- Dataset
    - https://drive.google.com/file/d/1bJOzTH4KyCZXKP99EG26m1mrp_C4eoq8/view?usp=sharing
- Right click on that project and go to Properties -> 디버깅 -> 명령 인수
    - PATH_TO_ORB_SLAM_FOLDER\Vocabulary\ORBvoc.txt PATH_TO_ORB_SLAM_FOLDER\Examples\Monocular\KITTI00-02.yaml PATH_TO_DATASET_FOLDER\dataset\sequences\SEQUENCE_NUMBER
- Right click on that project and go to 시작 프로그램으로 설정
- ctrl + F5 or F5

## 6. mono_webcam
- Right click on that project and go to Properties -> C/C++ -> Code Generation, and change Runtime Library to Multi-threaded (/MT). Then press apply
- Right click on it and press build
- Right click on that project and go to Properties -> 디버깅 -> 명령 인수
    - PATH_TO_ORB_SLAM_FOLDER\Vocabulary\ORBvoc.txt PATH_TO_ORB_SLAM_FOLDER\Examples\Monocular\logitech_c270.yaml
- Right click on that project and go to 시작 프로그램으로 설정
- ctrl + F5 or F5
