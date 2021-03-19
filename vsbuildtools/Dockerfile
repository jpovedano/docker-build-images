FROM mcr.microsoft.com/windows:1903

SHELL ["cmd", "/S", "/C"]

ADD https://github.com/git-for-windows/git/releases/download/v2.31.0.windows.1/Git-2.31.0-64-bit.exe "C:\tmp"
RUN "C:\tmp\Git-2.31.0-64-bit.exe /verysilent /norestart"

ADD "https://www.python.org/ftp/python/3.6.8/python-3.6.8-amd64.exe" "C:\tmp\python-3.6.8-amd64.exe"
RUN "C:\tmp\python-3.6.8-amd64.exe /wait /quiet InstallAllUsers=1 PrependPath=1"

ADD "https://cmake.org/files/v3.12/cmake-3.12.4-win64-x64.msi" "C:\tmp\cmake-installer.msi"
RUN "msiexec /i C:\tmp\cmake-installer.msi ALLUSERS=1 ADD_CMAKE_TO_PATH=System /quiet /passive"

ADD "https://strawberryperl.com/download/5.32.1.1/strawberry-perl-5.32.1.1-64bit.msi" "C:\tmp\perl-installer.msi"
RUN "msiexec /i C:\tmp\perl-installer.msi /quiet /passive" 

ADD https://aka.ms/vs/16/release/vs_buildtools.exe "C:\tmp\vs_buildtools.exe"
RUN "C:\tmp\vs_buildtools.exe --quiet --wait --norestart --nocache --installPath C:\BuildTools --add Microsoft.VisualStudio.Workload.MSBuildTools --add Microsoft.VisualStudio.Workload.VCTools --add Microsoft.VisualStudio.Component.VC.v141.x86.x64 --add Microsoft.VisualStudio.Component.VC.140 --add Microsoft.VisualStudio.Component.VC.Tools.x86.x64 --includeRecommended"

ENTRYPOINT [ "C:\\BuildTools\\Common7\\Tools\\VsDevCmd.bat", "-arch=x64", "&&", "cmd" ]