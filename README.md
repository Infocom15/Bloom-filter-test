Bloom-filter-test
=================
1, produceTraffic: Produce traffic file which contains random elements without duplicates.

Compile:  g++ -O2 traffic.cpp -o traffic

Run:      ./traffic 64 100000

==>       Means produce a traffic file with 102,400,000 elements without duplicates, and each element is 20 characters in length.

Detailed: 

First parameter: Bit length of the element use binary system, the actual element stored in the traffic file is in decimalism, which is 20 characters in length
So input 64, means the biggest element in the traffic file is 2^64-1=18446744073709551615, 20 characters in length.

Second parameter: Size of the traffic file, which will multiply by 1024 in the program, so input N will produce N*1024 elements  

Default parameter: If no other parameter input, only run as ./traffic, the code will use 64 as the first parameter and 1 as the second parameter.
This will produce a traffic file with 1,024 elements without duplicates, and each element is 20 characters in length.
        
2, sbf_linux: All the tests described in evaluation section of the paper. (Performance test on many-core is in folder sbf_linux_tile_muticore)

To run the specific test, you should comment out the corresponding test code in main().

!Need to modify the path in main.cpp first:  the const variable "fNamePrefix" should be your own folder path which contains the traffic file 

Compile:         make

Run:             ./sbf rand_20b_100M.tr(traffic file name) 20(length of the element in traffic file) 100(multiply by 1,000,000(M as a unit) in the program, so will search 100,000,000 elements)

Default parameter: 

If no other parameter input, only run as ./sbf, the code will run as "./sbf rand_20b_100M.tr 20 100" as described before.
                        
3, sbf_linux_tile_muticore: Insert the Telera TLR4-03680 platform into the linux PC and test the performance.
		    
!Need to modify the path in main.cpp first:  

the const variable "fNamePrefix" should be your own folder path which contains the traffic file 

the const variable "fNamePrefixOut" should be your own folder path which will store the result file 

Compile:        make

Run:            Use ./do.sh to test. Can modify it depend on your specific needs.

Default parameter:  Use the script do.sh to run the test, no need to use command line by yourself.   
