How To Build Header Only Boost
=====

Couple of scripts to build true header only Boost libraries.
Tested with Ubuntu 16.04 and Boost 1.70.0.

The main idea is to use Boost BCP tool on every library to find out if it produces 'src' folders in dependencies.
We don't want extra dependencies so will remove everything except 'src' in 'libs' (examples, docs).

## Prepare
Download and unpack Boost and remove everything unneeded.

```
./prepare.sh
```

## List
Prepare lists of libraries to extraction. Runs bcp on every library and collects dependencies.

Produces *header_only_libraries.txt* and *all_libraries.txt* (with dependencies).

```
./list.sh
```

<details><summary>expand</summary>
<p>

```
accumulators 24M
align 856K
any 1.7M
array 688K
assert 616K
assign 9.2M
bind 928K
callable_traits 368K
circular_buffer 2.8M
compatibility 132K
concept_check 2.3M
config 716K
container_hash 1.5M
conversion 24K
convert 36M
core 772K
crc 892K
detail 11M
disjoint_sets 44K
dynamic_bitset 9.8M
endian 1.8M
foreach 8.1M
format 4.2M
function 8.9M
function_types 10M
functional 16M
fusion 32M
hana 20M
headers 16K
heap 17M
histogram 11M
hof 504K
integer 792K
intrusive 3.3M
io 640K
iterator 16M
lambda 7.6M
lexical_cast 11M
local_function 9.8M
logic 672K
metaparse 12M
move 1.2M
mp11 208K
mpl 11M
msm 33M
multi_array 8.9M
multi_index 12M
optional 3.5M
parameter_python 20K
phoenix 40M
poly_collection 17M
polygon 2.1M
pool 1.8M
predef 684K
preprocessor 3.4M
property_tree 14M
proto 21M
ptr_container 12M
qvm 3.2M
ratio 7.8M
rational 1.6M
safe_numerics 1.3M
scope_exit 9.1M
signals2 19M
smart_ptr 2.7M
sort 4.5M
static_assert 632K
throw_exception 644K
tokenizer 8.0M
tti 11M
tuple 944K
type_index 3.3M
type_traits 2.1M
typeof 7.2M
units 17M
unordered 4.3M
utility 3.5M
uuid 12M
variant 9.8M
variant2 852K
vmd 2.9M
winapi 1.3M
xpressive 26M
yap 3.0M
```

</p>
</details>

## Extract
Run bcp to get final distributive.

```
./extract.sh
```

## Result
For those who are lazy here is the resulting bcp command line for the latest version (1.71):

```
bcp \
accumulators \
align \
any \
array \
assert \
assign \
bind \
callable_traits \
circular_buffer \
compatibility \
concept_check \
config \
container_hash \
conversion \
convert \
core \
crc \
detail \
disjoint_sets \
dynamic_bitset \
endian \
foreach \
format \
function \
functional \
function_types \
fusion \
hana \
headers \
heap \
histogram \
hof \
integer \
intrusive \
io \
iterator \
lambda \
lexical_cast \
local_function \
logic \
metaparse \
move \
mp11 \
mpl \
msm \
multi_array \
multi_index \
optional \
parameter_python \
phoenix \
poly_collection \
polygon \
pool \
predef \
preprocessor \
property_tree \
proto \
ptr_container \
qvm \
ratio \
rational \
safe_numerics \
scope_exit \
signals2 \
smart_ptr \
sort \
static_assert \
throw_exception \
tokenizer \
tti \
tuple \
type_index \
typeof \
type_traits \
units \
unordered \
utility \
uuid \
variant \
vmd \
winapi \
xpressive \
yap \
/tmp/boost
```

## Perl Package
There is a Perl package which contains some of the listed libraries:
* https://metacpan.org/pod/CPP::Boost::Mini

## Archive
* [Boost 1.68.0](archive/1_68_0/README.md)
* [Boost 1.69.0](archive/1_69_0/README.md)
* [Boost 1.70.0](archive/1_70_0/README.md)

## References
* https://www.boost.org/doc/libs/1_70_0/tools/bcp/doc/html/index.html
* https://www.boost.org/doc/libs/1_70_0/more/getting_started/unix-variants.html#header-only-libraries
* https://steveire.wordpress.com/2016/08/21/boost-dependencies-and-bcp/
* https://www.boost.org/doc/libs
* https://unix.stackexchange.com/questions/158234/tool-in-unix-to-subtract-text-files

