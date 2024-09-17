# Seidel
def gauss_seidel(A, b, x0, max_iterations=100, tolerance=1e-6):
    n = len(A)
    x = x0.copy()
    for _ in range(max_iterations):
        for i in range(n):
            sum_ax = sum(A[i][j] * x[j] for j in range(n) if j != i)
            x[i] = (b[i] - sum_ax) / A[i][i]
        if all(abs(x[i] - x0[i]) < tolerance for i in range(n)):
            break
        x0 = x.copy()
    return x
# Matriz de coeficientes
A = [[3, -0.1, -0.2],
     [0.1, 7, -0.3],
     [0.3, -0.2, 10]]
# Vector de términos independientes
b = [7.85, -19.3, 71.4]
# Aproximación inicial
x0 = [0, 0, 0]
# Llamada a la función gauss_seidel
solucion = gauss_seidel(A, b, x0)
# Imprimir la solución
print(f"La solución aproximada es: x1 = {solucion[0]}, x2 = {solucion[1]}, x3 = {solucion[2]}")
