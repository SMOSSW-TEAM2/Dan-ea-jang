# 그냥 함수 지정해서 불러오기 or txt나 yml로 저장해서 출력후 저장하기 or class로 불러오기

#===============언어===================
Language = ""  # 언어

#===============난이도=================
# 단어의 난이도 측정을 어떻게 할건가요?
Seconds = 0  # 문제당 시간
Count = 0  # 문제 개수
Life = 0  # 목숨 수

#=================색맹================
Color_Blindness = 0  # 색맹용 0이면 아니면 1
#=================난이도================
# random 문제 출제
# 맞으면 count+=1, 틀리면 Life -=1

class DJOptions:
    def Language(self, x):
        global lang
        lang = x

    def Count(self, x, wordbook):
        if x <= 0:
            print("문제 개수는 1 이상이어야 합니다.")
            return

        questions = generate_questions(wordbook, x)

        for i, question in enumerate(questions, start=1):
            print(f"Question {i}: {question}")
            answer = input("Answer: ")
            check_answer(question, answer)

            DJOptions.Life -= 1  # 라이프 감소
            if DJOptions.Life <= 0:
                print("Game Over")
                break

    def Life(self, x):
        if x <= 0:
            print("목숨은 1 이상이어야 합니다.")
            return

        DJOptions.Life = x
        print(f"목숨이 {x}개로 설정되었습니다.")

import random

def generate_questions(wordbook, count):
    # 문제를 저장할 리스트 생성
    questions = []

    # wordbook에서 count 개수만큼의 문제를 랜덤하게 선택하거나 생성하여 questions 리스트에 추가
    for _ in range(count):
        # wordbook에서 랜덤하게 단어 선택
        random_word = random.choice(wordbook)

        # 단어를 기반으로 문제 생성 또는 단어 그 자체를 문제로 사용
        question = generate_question_from_word(random_word)

        # 문제 리스트에 추가
        questions.append(question)

    # 생성된 문제 리스트 반환
    return questions

def generate_question_from_word(word):
    # 단어를 기반으로 문제 생성 또는 단어 그 자체를 문제로 사용하는 로직을 구현
    # 예를 들어, 단어의 뜻을 문제로 만들거나 단어의 알파벳을 섞어서 문제로 만들 수 있습니다.
    # 이 예시에서는 단어 그 자체를 문제로 사용하도록 가정합니다.
    return word


def check_answer(question, answer):
    # 정답을 제공합니다
    correct_answer = get_correct_answer(question)

    if answer == correct_answer:
        count += 1
        print("정답입니다!")
    else:
        life -= 1
        print("오답입니다!")

    print("맞은 개수:", count)
    print("남은 기회:", life)



   
