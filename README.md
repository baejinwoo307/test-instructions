graph LR
    %% Actors Definition
    Lender["👤 Seller/Lender<br>(공급자)"]
    Borrower["👤 Buyer/Borrower<br>(수요자)"]
    Admin["⚙️ Admin<br>(관리자)"]

    %% System Boundary
    subgraph Major_Share_System ["📦 Major Share System (System Boundary)"]
        direction TB
        Logic(("매매/대여/예약<br>제어 엔진"))
    end

    %% Interactions (Relationships)
    Lender -- "물품 등록, 요청 승인,<br>반납 확인" --> Logic
    Borrower -- "물품 검색, 매매/대여 신청,<br>예약 및 연장 요청" --> Logic
    
    Logic -- "거래 상태 알림,<br>예약 승계 통보" --> Lender
    Logic -- "물품 정보 제공,<br>연장 가능 여부 피드백" --> Borrower
    
    Admin -- "시스템 모니터링,<br>유저 및 게시물 관리" --> Logic

    %% Styling
    style Major_Share_System fill:#f9f9f9,stroke:#333,stroke-width:2px
    style Logic fill:#e1f5fe,stroke:#01579b
