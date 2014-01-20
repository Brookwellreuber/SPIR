<html>

<head>
<meta http-equiv=Content-Type content="text/html; charset=windows-1255">
<meta name=Generator content="Microsoft Word 14 (filtered)">
<style>
</style>

</head>

<body lang=EN-US>

<div class=WordSection1>

<p class=MsoPlainText style='margin-right:-34.3pt'><span style='font-family:
"Courier New"'>//===----------------------------------------------------------------------===//<br>
// SPIR generator/Clang Installation Instructions<br>
//===----------------------------------------------------------------------===//<br>
<br>
<br>
These instructions describe how to build, install and operate SPIR
generator/<br>
Clang.<br>
<br>
<br>
//===----------------------------------------------------------------------===//<br>
// Step 1: Organization<br>
//===----------------------------------------------------------------------===//<br>
<br>
<br>
SPIR generator/Clang is designed to be built as part of an LLVM build. <br>
SPIR generator/Clang is based on LLVM/Clang version 3.2<br>
<br>
The LLVM source code could be downloaded from:<br>
  http://www.llvm.org/releases/3.2/llvm-3.2.src.tar.gz<br>
  <br>
It is also available directly from the LLVM svn server:<br>
  svn co http://llvm.org/svn/llvm-project/llvm/tags/RELEASE_32/final llvm<br>
<br>
Or could be cloned from LLVM git repository:<br>
<br>
  git clone http://llvm.org/git/llvm.git llvm<br>
  cd llvm<br>
  git checkout --track -b release_32 remotes/origin/release_32<br>
 <br>
Assuming that the LLVM source code is located at $LLVM_SRC_ROOT, then the clang
<br>
source code should be installed as:<br>
<br>
  $LLVM_SRC_ROOT/tools/clang<br>
<br>
The directory is not required to be called clang, but doing so will allow
the<br>
LLVM build system to automatically recognize it and build it along with
LLVM.<br>
<br>
  cd $LLVM_SRC_ROOT/tools<br>
  git clone https://github.com/KhronosGroup/SPIR clang<br>
  cd clang<br>
  git checkout --track -b spir_12 remotes/origin/spir_12<br>
    <br>
  <br>
//===----------------------------------------------------------------------===//<br>
// Step 2: Configure and Build LLVM<br>
//===----------------------------------------------------------------------===//<br>
<br>
<br>
Configure and build your copy of LLVM (see
$LLVM_SRC_ROOT/GettingStarted.html<br>
for more information).<br>
<br>
<br>
Assuming you installed clang at $LLVM_SRC_ROOT/tools/clang then Clang
will<br>
automatically be built with LLVM. Otherwise, run 'make' in the Clang
source<br>
directory to build Clang.<br>
<br>
* Note: currently there might be failures in check_clang project.<br>
<br>
//===----------------------------------------------------------------------===//<br>
// Step 3: (Optional) Verify Your Build<br>
//===----------------------------------------------------------------------===//<br>
<br>
<br>
It is a good idea to run the Clang tests to make sure your build works<br>
correctly. From inside the Clang build directory, run 'make test' to run
the<br>
tests.<br>
<br>
<br>
//===----------------------------------------------------------------------===//<br>
// Step 4: Install Clang<br>
//===----------------------------------------------------------------------===//<br>
<br>
<br>
If you wish to run Clang from the generated binary directory, you may skip this
section.<br>
<br>
From inside the Clang build directory, run 'make install' to install the
Clang<br>
compiler and header files into the prefix directory selected when LLVM
was<br>
configured.<br>
<br>
<br>
The Clang compiler is available as 'clang' and 'clang++'. It supports a gcc
like command line<br>
interface. See the man page for clang (installed into
$prefix/share/man/man1)<br>
for more information.<br>
<br>
<br>
//===----------------------------------------------------------------------===//<br>
// Step 5: Creating SPIR binaries<br>
//===----------------------------------------------------------------------===//<br>
<br>
<br>
To create a SPIR binary from a valid OpenCL-C file (.cl), use the following
command<br>
lines:<br>
<br>
  clang -cc1 -emit-llvm-bc -triple &lt;triple&gt; &lt;OpenCL compile
options&gt; -cl-spir-compile-options &quot;&lt;OpenCL compile options&gt;&quot;
-include &lt;opencl_spir.h&gt; -o &lt;output&gt; &lt;input&gt;<br>
<br>
* &lt;triple&gt;: for 32 bit SPIR use spir-unknown-unknown, for 64 bit SPIR use
spir64-unknown-unknown.<br>
* Note: &lt;OpenCL compile options&gt; appears twice. The command line option
-cl-spir-compile-options &quot;&lt;OpenCL compile options&gt;&quot;<br>
  specifies the compile options that occur in the SPIR metadata.<br>
* &lt;opencl_spir.h&gt;: download opencl_spir.h from https://github.com/KhronosGroup/SPIR-Tools/blob/master/headers/opencl_spir.h<br>
<br>
<br>
 &nbsp;</span></p>

</div>

</body>

</html>
