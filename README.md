# Moja Biblioteka Numeryczna

Projekt na przedmiot "Metody Numeryczne". Jest to biblioteka C++ implementująca różne algorytmy numeryczne.

## Funkcjonalność

*   Rozwiązywanie układów równań liniowych (eliminacja Gaussa, dekompozycja LU)
*   Interpolacja (Lagrange, Newton)
*   Aproksymacja
*   Całkowanie numeryczne
*   Rozwiązywanie równań różniczkowych
*   Rozwiązywanie równań nieliniowych

## Jak zbudować i uruchomić (używając VS Code z CMake Tools)

1.  Otwórz folder z projektem w Visual Studio Code.
2.  Upewnij się, że masz zainstalowane rozszerzenia C/C++ i CMake Tools.
3.  VS Code powinien automatycznie skonfigurować projekt. Wybierz kompilator (np. z Visual Studio Build Tools).
4.  Na dolnym pasku stanu:
    *   Wybierz cel do uruchomienia: `[ExamplesApp]` lub `[TestsApp]`.
    *   Kliknij przycisk **Build**, aby skompilować projekt.
    *   Kliknij przycisk **Run (▶️)**, aby uruchomić wybrany program.

## Przykład użycia

```cpp
#include <iostream>
#include "linear_algebra.hpp"

int main() {
    std::vector<std::vector<double>> a = {{2, 1, -1}, {-3, -1, 2}, {-2, 1, 2}};
    std::vector<double> b = {8, -11, -3};
    
    auto result = gaussianElimination(a, b);
    if (result) {
        
    }
    return 0;
}

#include "interpolation.hpp"

std::vector<double> x_nodes = {0, 1, 2};
std::vector<double> y_nodes = {0, 1, 4}; 
double interpolated_value = lagrangeInterpolation(x_nodes, y_nodes, 1.5);


#include "approximation.hpp"
// ...
std::vector<double> x = {0, 1, 2};
std::vector<double> y = {1.1, 2.9, 5.2}; 
auto coeffs = polynomialApproximation(x, y, 1);



#include "integration.hpp"
// ...
auto func_to_integrate = [](double x){ return 3 * x * x; };
double integral = simpsonMethod(func_to_integrate, 0.0, 2.0, 100);



#include "differential_equations.hpp"

auto ode_func = [](double t, double y){ return y; };
auto solution_points = rk4Method(ode_func, 0, 1, 1.0, 0.1);
double final_y = solution_points.back().second;



#include "nonlinear_equations.hpp"

auto nonlinear_func = [](double x){ return x * x - 2.0; };
auto root = bisection(nonlinear_func, 1.0, 2.0);
if (root) {
   
}