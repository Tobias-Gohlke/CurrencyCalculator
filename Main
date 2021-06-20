import argparse
import math

parser = argparse.ArgumentParser()

parser.add_argument("--type", choices=["diff", "annuity"])
parser.add_argument("--principal")
parser.add_argument(("--payment"))
parser.add_argument("--periods")
parser.add_argument("--interest")

args = parser.parse_args()
if args.interest is not None:
    if args.type == "annuity":
        if args.payment is None:
            if args.principal is not None and args.periods is not None:
                P = float(args.principal)
                i = (float(args.interest) / 100) / 12
                n = int(args.periods)
                if P < 0 or i < 0 or n < 0:
                    print("Incorrect parameters")
                else:
                    A = int((round((P * ((i * (1 + i) ** n) / ((1 + i) ** n - 1))), 0)) + 1)
                    O = int(round(A * n - P, 0))
                    print(f"Your annuity payment = {A}!")
                    print(f"Overpayment = {O}")
            else:
                print("Incorrect parameters")
        elif args.periods == None:
            if args.principal is not None and args.payment is not None:
                P = float(args.principal)
                i = (float(args.interest) / 100) / 12
                A = float(args.payment)
                if P < 0 or i < 0 or A < 0:
                    print("Incorrect parameters")
                else:
                    n = math.log(A / (A - (i * P)), 1 + i)

                    if n % 1 != 0:
                        n = int(n) + 1
                        years = n // 12
                        month = n % 12
                    if years > 1:
                        y = "years"
                    else:
                        y = "year"
                    if month > 1:
                        m = "months"
                    else:
                        m = "month"
                    if years != 0 and month != 0:
                        print(f"It will take {years} {y} and {month} {m} to repay this loan!")
                    elif years == 0 and month != 0:
                        print(f"{month} {m}")
                    else:
                        print(f"{years} {y}")
                    print(f"Overpayment = {n * A - P}")
            else:
                print("Incorrect parameters")
        elif args.principal == None:
            if args.payment is not None and args.periods is not None:
                i = (float(args.interest) / 100) / 12
                A = float(args.payment)
                n = int(args.periods)
                if A < 0 or i < 0 or n < 0:
                    print("Incorrect parameters")
                else:
                    P = int(round(A / ((i * (1 + i) ** n) / ((1 + i) ** n - 1)), 0))
                    print(f"Your loan principal = {P}!")
                    O = int(round(A * n - P, 0))
                    print(f"Overpayment = {O}")
            else:
                print("Incorrect parameters")
    else:
        P = float(args.principal)
        n = int(args.periods)
        i = (float(args.interest) / 100) / 12
        m = 1
        Overz = 0
        if P is not None and n is not None:
            if P < 0 or n < 0 or i < 0:
                print("Incorrect parameters")
            else:
                for m in range(1, n + 1):
                    D = (P / n) + i * (P - ((P * (m - 1)) / (n)))
                    if D % 1 != 0:
                        D = int(D) + 1
                    else:
                        D = int(D)
                    Overz += D
                    print(f"Month {m}: payment is {int(round(D, 0))}")
                O = Overz - P
                print(f"Overpayment = {int(round(O))}")
        else:
            print("Incorrect parameters")
else:
    print("Incorrect parameters")
