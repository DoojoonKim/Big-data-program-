RFP 고객 정보 관리 시스템.

5개의 기능함수를 가지고 있는 이 시스템은
고객정보의 입력, 조회, 수정, 삭제 4가지의 데이터 조작 함수 그리고 이 4가지 중 사용할 기능을 선택하는 제어 함수로 구성됩니다

관리시스템을 실행하면 입력, 조회, 수정, 삭제중 어떤 기능을 사용할지 선택하는 제어함수가 호출됩니다.

# Q 입력을 이용한 프로그램 종료를 제어함수에 추가할 예정입니다.

----제어 함수------
----------------  |
|  S - 조회함수 |  |
|  I - 입력함수 |  |
|  U - 수정함수 |  |
|  D - 삭제함수 |  |
-------------------
입력 값에 따라 해당 기능을 가진 함수가 호출되며, 기능이 끝난뒤에는 다시 제어함수가 호출 되게 됩니다.
고객정보는 고객의 이름, 나이, 성별, 생일 정보값을 갖습니다. 


1. 조회함수
 조회함수는 저장된 DB에 저장되어있는 모든 고객정보를 우선 모두 가져오게 됩니다. 
 
 # 현재(18.10.04) 모든 정보를 우선 가져오기만 하지만 추후 DB로 넘어오는 고객정보들의 인덱스를 이용하여
   정보 페이지를 구성, P F  페이지의 이동을 구현할 예정입니다.
 
 # 구현계획은 우선 DB 쿼리문으로부터 가져와지는 데이터 형태를 파악하고, 출력 되기 전
   인덱싱이 용이하도록 필요시 데이터 타입을 조정할 것입니다. 조정된 고객정보 데이터를

2. 입력함수
  입력함수는 콘솔에 입력함과 동시에 연동된 고객정보가 DB Table인 customer_table에 추가가 됩니다.
  입력함수가 호출되면 4가지의 입력 요구사항을 순서대로 받습니다.
  
  2-1 '이름을 입력하세요' 
  2-2 '나이를 입력하세요' 
  2-3 '성별을 입력하세요'
  2-4 '생일을 입력하세요'
  
  4번의 입력을 통해서 각자 name, age, gender, birth 라는 변수에 할당이 된 뒤 customer_table에
  추가가 됩니다.
  
  # 현재(18.10.14)에서 각각의 정보를 입력 시킬수는 있지만 정해진 형식에 대한 예외처리를 추후
    추가할 예정입니다. 예외처리 구현은 While 반복문을 사용할 예정입니다. 
  
  # 이름의 경우 반드시 문자열로 구성되도록하고 이외에 숫자 혹은 특수문자가 입력되면 
    다시 입력을 받도록 할 예정입니다.
  
  # 성별의 경우 M 또는 F 만 입력 받을수 있도록 하고 그 외의 입력값을 받으면
    다시 입력을 받도록 할 예정입니다.
    
  # 이메일의 경우 문자열로 저장하며 '@'와 '.' 가 포함되지 않으면 잘못된 이메일 형식으로 간주하여
    다시 입력을 받도록 할 예정입니다.
  
  # 생년월일의 경우 6자리 정수로 받게 할것이며 자리수가 맞지 않거나 비정상적 생년 월일의 경우
    다시 입력을 받도록 할 예정입니다. 비정상적인 수치의 경우 월,일 형식을 따르지 않는 입력값을
    의미하며 또다른 예외를 생각 해 볼 예정입니다.
    
 3. 수정함수
   수정함수는 고객의 나이와 생년월일을 수정할 수 있도록 해주는 함수입니다. 3가지의 입력 요구사항을 받으며
   내용은 다음과 같습니다.
   
   3-1 '수정할 고객의 이름을 입력하시오'
   3-2 '수정할 고객의 나이를 다시 입력하시오'
   3-3 '수정할 생년월일을 다시 입력하시오'
   
   첫번째 요구사항인 입력된 이름이 고객정보 데이터베이스의 Primary Key로 수정될 데이터를 추적하는데 사용되며
   이후 다시 입력받는 나이와 생년월일이 해당 이름을 가진 고객 정보에서 수정되게 됩니다.
   
   # 데이터베이스에 없는 이름을 작성시 SQL 오류가 발생하게 되는데 이를 사용자가 명확히 식별 할 수있도록 예외 처리 오류문을
     추가할 예정입니다.
   # 고객의 나이와 생년월일에 비정상적인 수치에 대한 예외처리를 While문을 이용하여 추가할 예정입니다.
   # 비정상적인 수치에 대한 기준은 추후 논의후 결정할 예정입니다.
   
 4. 삭제함수
   데이터베이스에 입력되어있는 고객정보를 완전히 제거하는 함수입니다. 삭제할 고객의 이름을 입력 요구사항으로 받으며
   일치하는 이름의 고객정보를 삭제하게 됩니다.
   

   
