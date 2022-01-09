

.section .data
inp1: .asciz "%d"
inp2: .asciz "%lf"
output: .asciz "sum=%lf avg=%lf"
debug: .asciz "printed %lf %d"
n: .int 0
sm: .double 0
avg: .double 0
x: .double 0


.section .text
.globl _main

_main:
	
	
	pushl $n
	pushl $inp1
	call _scanf
	add $8, %esp
	
	movl $0,%ecx
	
	
input_loop:
	
	pushl %ecx
	
	pushl $x+4
	pushl $x
	pushl $inp2
	call _scanf
	add $12, %esp
	popl %ecx
		
	fldl x		# push to top
	faddl sm
	fstpl sm
	
	add $1, %ecx
	cmp %ecx,n
	ja input_loop

	
	fildl n		# convert n to double & load to top
	fldl sm		# load to top
	fdivp %st(0), %st(1)	# divide top 2  (sm/n)
	fstpl avg	# store avg after loading in it
	
	pushl avg+4	# push avg to stack
	pushl avg
	pushl sm+4	# push sum to stack
	pushl sm
	pushl $output
	call _printf

	add $20,%esp
	
	ret


# gcc -O3 -o arch.exe arch.s
	
	
