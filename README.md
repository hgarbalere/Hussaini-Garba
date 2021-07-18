Tasks 3

// CPP program to find count of
// primes in given array.
#include <bits/stdc++.h>

using namespace std;
 
// Function to find count of prime

int primeCount(int arr[], int n)
{

    // Find maximum value in the array

    int max_val = *max_element(arr, arr+n);
 

    // USE SIEVE TO FIND ALL PRIME NUMBERS LESS

    // THAN OR EQUAL TO max_val

    // Create a boolean array "prime[0..n]". A

    // value in prime[i] will finally be false

    // if i is Not a prime, else true.

    vector<bool> prime(max_val + 1, true);
 

    // Remaining part of SIEVE

    prime[0] = false;

    prime[1] = false;

    for (int p = 2; p * p <= max_val; p++) {
 

        // If prime[p] is not changed, then

        // it is a prime

        if (prime[p] == true) {
 

            // Update all multiples of p

            for (int i = p * 2; i <= max_val; i += p)

                prime[i] = false;

        }

    }
 

    // Find all primes in arr[]

    int count = 0;

    for (int i = 0; i < n; i++) 

        if (prime[arr[i]])

            count++;    
 

    return count;
}
 
// Driver code

int main()
{
 

    int arr[] = { 1, 2, 3, 4, 5, 6, 7 };

    int n = sizeof(arr) / sizeof(arr[0]);
 

    cout << primeCount(arr, n);
 

    return 0;
}
