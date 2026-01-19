# ----- 학생 성적 프로그램 -----
SUBJECTS = ("국어", "영어", "수학", "과학")

# 1. 학생을 추가하는 함수 add_student() 작성
# - "[이름] 학생이 추가되었습니다." 반환
# - (선택) 이미 존재하는 이름일 경우 "이미 존재하는 학생입니다." 반환
def add_student(students, name):
    if name in students:
        return "이미 존재하는 학생입니다."
    students[name] = {s: 0 for s in SUBJECTS}
    # 저장 예시
    # students = {
    # "김재섭" : {"국어":0, "영어":0, "수학":0, "과학":0}
    # }
    return f"{name} 학생이 추가되었습니다."

# 2. 학생을 삭제하는 함수 remove_student() 작성
# -[이름] 학생이 삭제되었습니다." 반환
# - (선택) 존재하는 이름이 없을 경우 "해당 학생이 없습니다." 반환
def remove_student(students, name):
    if name not in students:
        return "해당 학생이 없습니다."
    students.pop(name)
    return f"{name} 학생이 삭제되었습니다."

# 3. 점수를 저장하는 함수 set_score() 작성
# - "[이름] 학생의 [과목] 점수가 [점수]로 저장되었습니다." 반환
# - (선택) 존재하는 이름이 없을 경우 "해당 학생이 없습니다." 반환
# - (선택) 존재하는 과목이 없을 경우 "존재하지 않는 과목입니다." 출력
# - (선택) 점수가 0 미만 또는 100 초과일 경우 "점수는 0~100점 사이여야 합니다." 출력
def set_score(students, name, subject, scores):
    if name not in students:
      return "해당 학생이 없습니다"
    if subject not in SUBJECTS:
      return "존재하지 않는 과목입니다."
    if scores < 0 or scores > 100:
      return "점수는 0~100점 사이여야 합니다."
    return f"{name} 학생의 {subject} 점수가 {scores}로 저장되었습니다."

# 4. 특정 학생의 합계 점수를 반환하는 함수 student_total() 작성
# - 학생의 합계 점수를 반환
# - (선택) 존재하는 이름이 없을 경우 "None" 반환
def student_total(students, name):
  if name not in students:
    return None
  return sum(students[name].values)

# 5. 특정 학생의 평균 점수를 반환하는 함수 student_avg() 작성
# - 학생의 평균 점수 반환
# - (선택) 존재하는 이름이 없을 경우 "None" 반환
def student_avg(students, name):
  if name not in students:
    return None
  return (sum(students[name].values)) / len(SUBJECTS)

# 6. 학생 정보를 출력하는 함수 print_student() 작성
# - "총점: [합계], 평균: [평균]" 출력
# - (선택) 존재하는 이름이 없을 경우 "해당 학생이 없습니다." 출력
def print_student(students, name):
  if name not in students:
      return "해당 학생이 없습니다"
  print("총점: " )

# 7. 학생들의 전체 리스트를 조회하는 함수 print_all() 작성
# - 전체 학생의 이름을 출력
# - (선택) 학생 목록이 없을 경우 "학생 목록이 비어 있습니다." 출력
def print_all(students):
  if not students:
    return "학생 목록이 비어 있습니다."
  for s in students:
    print(s)

# ---------------------------------------------------------------------
def run_students():
    students = {}
    while True:
        print("\n=== 학생 성적 프로그램 ===")
        print("1. 학생 추가")
        print("2. 학생 삭제")
        print("3. 점수 입력/수정")
        print("4. 학생 성적 조회")
        print("5. 전체 학생 목록")
        print("0. 종료")
        choice = input("번호: ").strip()

        # 학생의 이름을 입력받고 add_student() 함수를 호출 및 반환된 문자열을 출력하세요.
        if choice == "1":
            name = input("추가할 학생 이름: ")
            msg = add_student(students, name)
            print(msg)

        elif choice == "2":
        # 삭제할 학생의 이름을 입력받고 remove_student() 함수를 호출 및 반환된 문자열을 출력하세요.
            name = input("삭제할 학생 이름:")
            msg = remove_student(students, name)
            print(msg)

        elif choice == "3":
        # 학생의 이름, 과목(국어/영어/수학/과학), 점수를 입력받고 set_score() 함수를 호출 및 반환된 문자열을 출력하세요.
            name = input("학생의 이름을 입력하세요: ")
            subject = input("과목(국어/영어/수학/과학)을 입력하세요: ")
            score = input("점수를 입력하세요: ")
            msg = set_score(students, name, subject, score)
            print(msg)

        elif choice == "4":
        # 조회할 학생의 이름을 입력받고 print_student() 함수를 호출하세요.
            name - input("조회할 학생의 이름을 입력하세요: ")
            print_student(students,name)

        elif choice == "5":
        # print_all() 함수를 호출하세요.
            print_all(students)

        elif choice == "0":
        # "프로그램을 종료합니다"를 출력하고 반복문을 종료하세요.
            print("프로그램을 종료합니다")
            break

        else:
          print("잘못된 입력입니다.")



run_students()

