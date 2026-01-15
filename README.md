"""
중학교 1학년 기술교과 성적 데이터 생성기
- 기말고사: 60점 만점
- 수행평가 1, 2, 3: 각각 배점 설정
- 5개 반, 각 반 30명
"""

import random
import csv
from datetime import datetime

# 설정
NUM_CLASSES = 5  # 반 개수
STUDENTS_PER_CLASS = 30  # 반별 학생 수
FINAL_EXAM_MAX = 60  # 기말고사 만점
PERFORMANCE_1_MAX = 15  # 수행평가 1 만점
PERFORMANCE_2_MAX = 15  # 수행평가 2 만점
PERFORMANCE_3_MAX = 10  # 수행평가 3 만점
TOTAL_MAX = FINAL_EXAM_MAX + PERFORMANCE_1_MAX + PERFORMANCE_2_MAX + PERFORMANCE_3_MAX

# 한국 성씨와 이름
last_names = ["김", "이", "박", "최", "정", "강", "조", "윤", "장", "임", "한", "오", "서", "신", "권", "황", "안", "송", "류", "홍"]
first_names_boy = ["민준", "서준", "도윤", "예준", "시우", "주원", "하준", "지호", "지후", "준서", "건우", "우진", "선우", "연우", "유준", "정우", "승우", "승현", "시윤", "준혁"]
first_names_girl = ["서윤", "서연", "지우", "서현", "민서", "하은", "하윤", "윤서", "지민", "지유", "채원", "지안", "수아", "소율", "예은", "예린", "다은", "은서", "수빈", "지원"]

def generate_student_name(student_num):
    """학생 이름 생성"""
    last_name = random.choice(last_names)
    if student_num % 2 == 0:
        first_name = random.choice(first_names_boy)
    else:
        first_name = random.choice(first_names_girl)
    return last_name + first_name

def generate_score(max_score, difficulty="normal"):
    """
    점수 생성 (정규분포 기반)
    difficulty: easy(평균 높음), normal(중간), hard(평균 낮음)
    """
    if difficulty == "easy":
        mean = max_score * 0.85
        std_dev = max_score * 0.10
    elif difficulty == "hard":
        mean = max_score * 0.70
        std_dev = max_score * 0.15
    else:  # normal
        mean = max_score * 0.78
        std_dev = max_score * 0.12
    
    score = random.gauss(mean, std_dev)
    score = max(0, min(max_score, score))  # 0 ~ max_score 범위로 제한
    return round(score, 1)

def calculate_grade_by_rank(rank, total_students):
    """
    등급 계산 (상대평가 기준)
    A: 상위 20% (30명)
    B: 상위 21~50% (45명)
    C: 상위 51~80% (45명)
    D: 상위 81~95% (22명)
    E: 하위 5% (8명)
    """
    percentile = (rank / total_students) * 100
    
    if percentile <= 20:
        return "A"
    elif percentile <= 50:
        return "B"
    elif percentile <= 80:
        return "C"
    elif percentile <= 95:
        return "D"
    else:
        return "E"

# 전체 학생 데이터 생성
all_students = []

print("=" * 80)
print("중학교 1학년 기술교과 성적 데이터 생성")
print("=" * 80)
print(f"기말고사: {FINAL_EXAM_MAX}점 만점")
print(f"수행평가 1: {PERFORMANCE_1_MAX}점 만점")
print(f"수행평가 2: {PERFORMANCE_2_MAX}점 만점")
print(f"수행평가 3: {PERFORMANCE_3_MAX}점 만점")
print(f"총점: {TOTAL_MAX}점 만점")
print("=" * 80)

for class_num in range(1, NUM_CLASSES + 1):
    print(f"\n[{class_num}반 성적 생성 중...]")
    
    for student_num in range(1, STUDENTS_PER_CLASS + 1):
        # 학생 정보
        student_id = f"{class_num}{student_num:02d}"
        name = generate_student_name(student_num)
        
        # 점수 생성 (각 평가마다 난이도를 약간씩 다르게)
        final_exam = generate_score(FINAL_EXAM_MAX, "normal")
        performance_1 = generate_score(PERFORMANCE_1_MAX, "easy")
        performance_2 = generate_score(PERFORMANCE_2_MAX, "normal")
        performance_3 = generate_score(PERFORMANCE_3_MAX, "easy")
        
        # 총점 계산 (등급은 나중에 상대평가로 계산)
        total_score = final_exam + performance_1 + performance_2 + performance_3
        
        # 데이터 저장 (등급은 임시로 None)
        student_data = {
            "반": class_num,
            "번호": student_num,
            "학생ID": student_id,
            "이름": name,
            "기말고사": final_exam,
            "수행평가1": performance_1,
            "수행평가2": performance_2,
            "수행평가3": performance_3,
            "총점": round(total_score, 1),
            "등급": None
        }
        
        all_students.append(student_data)
    
    print(f"  ✓ {class_num}반 30명 생성 완료")

print(f"\n총 {len(all_students)}명의 학생 데이터 생성 완료!")

# 상대평가로 등급 계산 (전체 학생을 총점 기준으로 정렬 후 등급 부여)
print("\n상대평가 등급 계산 중...")
sorted_students = sorted(all_students, key=lambda x: x["총점"], reverse=True)

for rank, student in enumerate(sorted_students, start=1):
    grade = calculate_grade_by_rank(rank, len(all_students))
    student["등급"] = grade

print("✓ 등급 계산 완료!\n")

# CSV 파일로 저장
csv_filename = "tech_scores.csv"
with open(csv_filename, "w", encoding="utf-8-sig", newline="") as csvfile:
    fieldnames = ["반", "번호", "학생ID", "이름", "기말고사", "수행평가1", "수행평가2", "수행평가3", "총점", "등급"]
    writer = csv.DictWriter(csvfile, fieldnames=fieldnames)
    
    writer.writeheader()
    for student in all_students:
        writer.writerow(student)

print(f"✓ CSV 파일 저장 완료: {csv_filename}")

# 반별 통계 출력
print("\n" + "=" * 80)
print("반별 통계")
print("=" * 80)

for class_num in range(1, NUM_CLASSES + 1):
    class_students = [s for s in all_students if s["반"] == class_num]
    
    avg_final = sum(s["기말고사"] for s in class_students) / len(class_students)
    avg_perf1 = sum(s["수행평가1"] for s in class_students) / len(class_students)
    avg_perf2 = sum(s["수행평가2"] for s in class_students) / len(class_students)
    avg_perf3 = sum(s["수행평가3"] for s in class_students) / len(class_students)
    avg_total = sum(s["총점"] for s in class_students) / len(class_students)
    
    print(f"\n[{class_num}반]")
    print(f"  기말고사 평균: {avg_final:.1f}/{FINAL_EXAM_MAX}")
    print(f"  수행평가1 평균: {avg_perf1:.1f}/{PERFORMANCE_1_MAX}")
    print(f"  수행평가2 평균: {avg_perf2:.1f}/{PERFORMANCE_2_MAX}")
    print(f"  수행평가3 평균: {avg_perf3:.1f}/{PERFORMANCE_3_MAX}")
    print(f"  총점 평균: {avg_total:.1f}/{TOTAL_MAX}")
    
    # 등급 분포
    grade_count = {}
    for student in class_students:
        grade = student["등급"]
        grade_count[grade] = grade_count.get(grade, 0) + 1
    
    print(f"  등급 분포: ", end="")
    for grade in ["A", "B", "C", "D", "E"]:
        count = grade_count.get(grade, 0)
        print(f"{grade}:{count}명 ", end="")
    print()

# 전체 통계
print("\n" + "=" * 80)
print("전체 통계 (5개 반 150명)")
print("=" * 80)

avg_final_all = sum(s["기말고사"] for s in all_students) / len(all_students)
avg_perf1_all = sum(s["수행평가1"] for s in all_students) / len(all_students)
avg_perf2_all = sum(s["수행평가2"] for s in all_students) / len(all_students)
avg_perf3_all = sum(s["수행평가3"] for s in all_students) / len(all_students)
avg_total_all = sum(s["총점"] for s in all_students) / len(all_students)

print(f"기말고사 평균: {avg_final_all:.1f}/{FINAL_EXAM_MAX}")
print(f"수행평가1 평균: {avg_perf1_all:.1f}/{PERFORMANCE_1_MAX}")
print(f"수행평가2 평균: {avg_perf2_all:.1f}/{PERFORMANCE_2_MAX}")
print(f"수행평가3 평균: {avg_perf3_all:.1f}/{PERFORMANCE_3_MAX}")
print(f"총점 평균: {avg_total_all:.1f}/{TOTAL_MAX}")

# 전체 등급 분포
grade_count_all = {}
for student in all_students:
    grade = student["등급"]
    grade_count_all[grade] = grade_count_all.get(grade, 0) + 1

print(f"\n전체 등급 분포:")
for grade in ["A", "B", "C", "D", "E"]:
    count = grade_count_all.get(grade, 0)
    percentage = (count / len(all_students)) * 100
    print(f"  {grade}: {count}명 ({percentage:.1f}%)")

# 상위 10명 출력
print("\n" + "=" * 80)
print("전체 상위 10명")
print("=" * 80)

top_10 = sorted(all_students, key=lambda x: x["총점"], reverse=True)[:10]
print(f"{'순위':<6}{'반':<6}{'번호':<6}{'이름':<10}{'기말':<8}{'수행1':<8}{'수행2':<8}{'수행3':<8}{'총점':<8}{'등급':<6}")
print("-" * 80)

for rank, student in enumerate(top_10, start=1):
    print(f"{rank:<6}{student['반']:<6}{student['번호']:<6}{student['이름']:<10}"
          f"{student['기말고사']:<8.1f}{student['수행평가1']:<8.1f}{student['수행평가2']:<8.1f}"
          f"{student['수행평가3']:<8.1f}{student['총점']:<8.1f}{student['등급']:<6}")

print("\n" + "=" * 80)
print(f"데이터 생성 완료 시간: {datetime.now().strftime('%Y-%m-%d %H:%M:%S')}")
print("=" * 80)
# 37ansu37.github.io
