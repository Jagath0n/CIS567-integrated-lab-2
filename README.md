# CIS567-integrated-lab-2
Code from my week 6 integrated lab

def check_singles(dice, goal):
    return sum(d for d in dice if d == goal)

def check_three_of_kind(dice):
    for i in range(len(dice) - 2):
        if dice[i] == dice[i+1] == dice[i+2]:
            return 30
    return 0

def check_four_of_kind(dice):
    for i in range(len(dice) - 3):
        if dice[i] == dice[i+1] == dice[i+2] == dice[i+3]:
            return 40
    return 0

def check_five_of_kind(dice):
    if dice[0] == dice[4]:
        return 50
    return 0

def check_full_house(dice):
    if (dice[0] == dice[1] and dice[2] == dice[4]) or (dice[0] == dice[2] and dice[3] == dice[4]):
        return 35
    return 0

def check_straight(dice):
    if dice == [1, 2, 3, 4, 5] or dice == [2, 3, 4, 5, 6]:
        return 45
    return 0

def find_high_score(dice):
    scores = [
        check_singles(dice, 1),
        check_singles(dice, 2),
        check_singles(dice, 3),
        check_singles(dice, 4),
        check_singles(dice, 5),
        check_singles(dice, 6),
        check_three_of_kind(dice),
        check_four_of_kind(dice),
        check_five_of_kind(dice),
        check_full_house(dice),
        check_straight(dice)
    ]
    return max(scores)

def main():
    dice = list(map(int, input().split()))
    dice.sort()
    high_score = find_high_score(dice)
    print(f"High score: {high_score}")

if __name__ == "__main__":
    main()
