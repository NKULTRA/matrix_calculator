def addition():
    matrix_a, rows_a, columns_a = read_matrix("first")
    matrix_b, rows_b, columns_b = read_matrix("second")
    if rows_a != rows_b or columns_a != columns_b:
        print("The operation cannot be performed.")
    else:
        print("The result is:")
        for i in range(rows_a):
            for j in range(columns_a):
                print(str(float(matrix_a[i][j]) + float(matrix_b[i][j])), end=" ")
            print("\n", end="")


def scalar_mult():
    matrix, rows, columns = read_matrix("the")
    constant = float(input("Enter constant: "))
    print("The result is:")
    for i in range(rows):
        for j in range(columns):
            print(str(float(matrix[i][j]) * constant), end=" ")
        print("\n", end="")


def multi():
    matrix_a, rows_a, columns_a = read_matrix("first")
    matrix_b, rows_b, columns_b = read_matrix("second")
    if columns_a != rows_b:
        print("The operation cannot be performed.")
    else:
        print("The result is:")
        i = 0
        counter = 0
        while i < rows_a:
            sums = j = 0
            while j < rows_b:
                sums += float(matrix_a[i][j]) * float(matrix_b[j][counter])
                j += 1
            print(str(sums), end=" ")
            if counter < columns_b - 1:
                counter += 1
            else:
                i += 1
                counter = 0
                print("\n", end="")


def calc_det(matrix, rows, columns):
    if rows == columns == 1:
        return float(matrix[0][0])
    elif rows == columns == 2:
        return float(matrix[0][0]) * float(matrix[1][1]) \
               - float(matrix[0][1]) * float(matrix[1][0])
    else:
        det = 0
        for i in range(columns):
            det += ((-1)**i) * float(matrix[0][i]) * \
                   calc_det([element[:i]+element[i+1:] for element in matrix[1:]], rows - 1, columns - 1)
        return det


def read_matrix(string):
    rows, columns = [int(x) for x in input("Enter size of " + string + " matrix: ").split(" ")]
    print("Enter " + string + " matrix:")
    return [input().split() for _ in range(rows)], rows, columns


def trans_main_diag():
    matrix, rows, columns = read_matrix("the")
    print("The result is:")
    for i in range(columns):
        for j in range(rows):
            print(matrix[j][i], end=" ")
        print("\n", end="")


def trans_side_diag():
    matrix, rows, columns = read_matrix("the")
    print("The result is:")
    for i in range(columns-1,-1,-1):
        for j in range(rows-1,-1,-1):
            print(matrix[j][i], end=" ")
        print("\n", end="")


def trans_vert():
    matrix, rows, columns = read_matrix("the")
    print("The result is:")
    for i in range(rows):
        for j in range(columns-1,-1,-1):
            print(matrix[i][j], end=" ")
        print("\n", end="")


def trans_horiz():
    matrix, rows, columns = read_matrix("the")
    print("The result is:")
    for i in range(rows-1,-1,-1):
        for j in range(columns):
            print(matrix[i][j], end=" ")
        print("\n", end="")


def menu_trans():
    print("1. Main diagonal")
    print("2. Side diagonal")
    print("3. Vertical line")
    print("4. Horizontal line")
    choice = input("Your choice: ")
    if choice == "1":
        trans_main_diag()
    elif choice == "2":
        trans_side_diag()
    elif choice == "3":
        trans_vert()
    elif choice == "4":
        trans_horiz()


def inverse():
    matrix, rows, columns = read_matrix("the")
    newmatrix = []
    if calc_det(matrix, rows, columns) == 0:
        print("This matrix doesn't have an inverse.")
        print()
        return 0

    for i in range(rows):
        for j in range(columns):
            newmatrix.append(((-1)**(i+j)) * \
        calc_det([element[:j] + element[j+1:] for element in matrix[:i] + matrix[i+1:]], rows-1, columns-1))
    newmatrix = [[newmatrix[i+j] for j in range(rows)] for i in range(0, len(newmatrix), columns)]
    print("The result is:")
    # here is just the Transposition, would be better to call
    # the function, but then I would have have to handle the input differently
    for i in range(columns):
        for j in range(rows):
            print(round((1 / calc_det(matrix, rows, columns)) * newmatrix[j][i], 2), end=" ")
        print("\n", end="")


def menu():
    while True:
        print("1. Add matrices")
        print("2. Multiply matrix by a constant")
        print("3. Multiply matrices")
        print("4. Transpose matrix")
        print("5. Calculate a determinant")
        print("6. Inverse matrix")
        print("0. Exit")
        choice = input("Your choice: ")
        if choice == "1":
            addition()
        elif choice == "2":
            scalar_mult()
        elif choice == "3":
            multi()
        elif choice == "4":
            menu_trans()
        elif choice == "5":
            matrix, rows, columns = read_matrix("the")
            print("The result is:")
            print(calc_det(matrix, rows, columns))
        elif choice == "6":
            inverse()
        elif choice == "0":
            break


# start of the program
menu()
