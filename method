import numpy as np

def validate_input(value):
    try:
        value = float(value)
        if value <= 0:
            raise ValueError
        return value
    except ValueError:
        print("Ошибка ввода! Введите положительное число.")
        return None


def enter_comparison(criteria):
    comparison_matrix = np.zeros((len(criteria), len(criteria)))

    for i in range(len(criteria)):
        for j in range(i + 1, len(criteria)):
            comparison = None
            while comparison is None:
                comparison = validate_input(
                    input(f"Введите относительную важность между критериями {criteria[i]} и {criteria[j]}: "))

            comparison_matrix[i, j] = comparison
            comparison_matrix[j, i] = 1 / comparison

    return comparison_matrix


def calculate_weights(comparison_matrix):
    matrix_sum = np.sum(comparison_matrix, axis=1)
    weights = matrix_sum / len(comparison_matrix)
    normalized_weights = weights / np.sum(weights)

    return normalized_weights


def main():
    criteria_count = None
    while criteria_count is None:
        criteria_count = int(input("Введите количество критериев: "))
        if criteria_count < 2:
            print("Ошибка ввода! Введите число больше 1.")
            criteria_count = None

    criteria = []
    for i in range(criteria_count):
        criteria.append(input(f"Введите название критерия {i + 1}: "))

    comparison_matrix = enter_comparison(criteria)

    weights = calculate_weights(comparison_matrix)

    for i in range(len(criteria)):
        print(f"Весовой коэффициент критерия {criteria[i]}: {weights[i]:.2f}")


main()