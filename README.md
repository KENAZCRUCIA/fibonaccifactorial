# fibonaccifactorial

EB3/61547/22 MICHEL BRIAN

import time

def factorial_recursive(n):
    return 1 if n <= 1 else n * factorial_recursive(n - 1)

def factorial_iterative(n):
    result = 1
    for i in range(2, n + 1):
        result *= i
    return result

def fibonacci_recursive(n):
    return n if n <= 1 else fibonacci_recursive(n - 1) + fibonacci_recursive(n - 2)

def fibonacci_iterative(n):
    if n <= 1:
        return n
    a, b = 0, 1
    for _ in range(2, n + 1):
        a, b = b, a + b
    return b

def measure_time(func, *args):
    start = time.time()
    func(*args)
    return (time.time() - start) * 1e9  # Convert to nanoseconds

def main():
    n = int(input("Enter a number: "))

    print(f"\nFactorial ({n}):")
    factorial_rec_time = measure_time(factorial_recursive, n)
    factorial_itr_time = measure_time(factorial_iterative, n)
    print(f"Recursive Result: {factorial_recursive(n)}")
    print(f"Iterative Result: {factorial_iterative(n)}")
    print(f"Recursive Time: {factorial_rec_time:.0f} ns")
    print(f"Iterative Time: {factorial_itr_time:.0f} ns")

    print(f"\nFibonacci ({n}):")
    fibonacci_rec_time = measure_time(fibonacci_recursive, n)
    fibonacci_itr_time = measure_time(fibonacci_iterative, n)
    print(f"Recursive Result: {fibonacci_recursive(n)}")
    print(f"Iterative Result: {fibonacci_iterative(n)}")
    print(f"Recursive Time: {fibonacci_rec_time:.0f} ns")
    print(f"Iterative Time: {fibonacci_itr_time:.0f} ns")

if __name__ == "__main__":
    main()
