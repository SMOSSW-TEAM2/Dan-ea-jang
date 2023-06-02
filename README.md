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

def generate_questions(wordbook, count):
    # 문제를 생성하는 로직을 구현해야 합니다.
    # wordbook에서 count 개수만큼의 문제를 랜덤하게 선택하거나 생성합니다.
    # 문제 리스트를 반환합니다.
    pass

def check_answer(question, answer):
    # 사용자의 답(answer)을 정답과 비교하는 로직을 구현해야 합니다.
    # 답이 맞으면 count를 증가시키고, 틀리면 Life를 감소시킵니다.
    # 결과를 출력합니다.
    pass


   
