# 1. Major Share (전공 자산 선순환 네트워크)

| Student No | 22211987 |
| :--- | :--- |
| Name | 배진우|
| E-mail | ajdjjaja292983474@gmail.com |


## [ Revision history ]
| Revision date | Version # | Description | Author |
| :--- | :--- | :--- | :--- |
| 2026/03/27 | 1.00 | First draft | 배진우 |

## = Contents =
1. [Business purpose](#1-business-purpose)
2. [System context diagram](#2-system-context-diagram)
3. [Use case list](#3-use-case-list)
4. [Concept of operation](#4-concept-of-operation)
5. [Problem statement](#5-problem-statement)
6. [Glossary](#6-glossary)
7. [References](#7-references)

---

## 1. Business purpose
- **Project background & Motivation:** 매 학기 시작마다 대학 생활 중 요구되는 전공및 교양 서적과 실험 기자재(ex 아두이노, 라즈베리 파이) 구입비는 적게는 수만 원에서 많게는 수십만 원에 달하는 가격입니다. 이 가격은 대학생들에게는 꽤나 큼 부담을 주는 금액들입니다. 게다가 이러한 자산들은 특정 학기의 수업 기간에만 집중적으로 사용된 후 나머지 기간에는 유휴 자산으로 방치되는 경우가 많고 추후에 사용하더라도 자원 활용의 효율성이 낮습니다.이러한 부담을 줄이는 방법인 에브리타임이나 당근마켓과 같은 기존 중고 거래 플랫폼은 존재하지만 이러한 플랫폼들은 일회성 매매에만 편중되어 있습니다.특히나 전공서적의 경우 지금 당장은 사용하지않더라도 추후에 사용할 가능성이 꽤나 크기에 매매를 하는것은 다소 꺼려질 수 있습니다.또한 단기간만 물건이 필요한 학생들에게는 매번 사고파는 과정이 번거로울 뿐만 아니라 대여를 원하더라도 신뢰할 수 있는 중개 시스템과 반납 확인 로직이 없어 개인 간 대여가 활성화되지 못하고 있습니다.이러한 환경은 학생들의 경제적 부담을 가중시킬 뿐만 아니라, 캠퍼스 내 자원의 효율적 배분을 저해하는 요소가 됩니다.따라서 자산의 소유권을 완전히 이전하는 매매와 일시적인 사용권을 공유하는 대여를 모두 가능하게 해줄 새로운 대안이 필요합니다.
- **Goal:** Major Share는 전공 자산의 매매와 대여를 통합 관리하는 플랫폼입니다. 특히 실시간 예약 및 자동 연장 제어 시스템을 통해 자원 독점을 방지하고 활용도를 극대화하여 공정한 선순환 경제를 형성하는 것이 목표입니다.
- **Target market:** 전국의 대학생들.

## 2. System context diagram

<img width="806" height="604" alt="system_context_diagram_" src="https://github.com/user-attachments/assets/48d47081-b9c8-4e30-8453-873324090618" />


* **Login :** 로그인
* **Register Item :** 판매/대여 물품 상세 정보 등록
* **Search & Filter :** 카테고리 및 거래 방식별 물품 검색 요청
* **Request Transaction :** 매매 구매 또는 대여/예약 신청 전송
* **Request Extension :** 대여 중인 물품의 반납 기한 연장 신청
* **Reserve Item :** 대여 중인 물품에 대한 차기 대기 예약 신청
* **Manage Requests :** 공급자의 거래/연장/예약 요청 승인 및 거절
* **Auto-Succession Alert :** 반납 완료 시 예약자에게 권한 자동 승계 알림
* **Block Extension Feedback :** 예약자 존재 시 대여자의 연장 신청 차단 피드백
* **Confirm Pickup/Return :** 물품 수령 및 반납 상호 인증
* **Transaction Review :** 거래 종료 후 물품 상태 및 유저 매너 평가 기록
* **System Monitoring :** 시스템 로그 및 이상 거래 데이터 모니터링

## 3. Use case list

### 1) Login
| **Actor** | Seller/Lender,Buyer/Borrower/Admin |
| :--- | :--- |
| **Description** | 각자 자신의 계정으로 로그인하고 올바른 정보를 입력했다면 로그인에 성공하게 된다. |

### 2) Register Item
| **Actor** | Seller/Lender |
| :--- | :--- |
| **Description** | 판매 또는 대여하고자 하는 전공 자산의 상세 정보(상태, 가격, 대여 기간 등)를 시스템에 등록한다. |

### 3) Request Extension
| **Actor** | Buyer/Borrower |
| :--- | :--- |
| **Description** | 대여 중인 물품의 기간 연장을 신청한다. 단, 예약 대기자가 없을 때만 시스템에 의해 활성화된다. |

### 4) Reserve Item
| **Actor** | Buyer/Borrower |
| :--- | :--- |
| **Description** | 현재 타 사용자가 이용 중인 물품에 대해 차기 대여 예약을 신청한다. |

### 5) Accept Reservation
| **Actor** | Seller/Lender |
| :--- | :--- |
| **Description** | 들어온 예약 신청 목록을 확인하고 특정 사용자의 예약 요청을 승인하여 우선권을 부여한다. |

### 6) Auto-Succession
| **Actor** | System |
| :--- | :--- |
| **Description** | 기존 대여자의 반납이 완료되면 승인된 차기 예약자에게 자동으로 대여 권한 및 알림을 승계한다. |

### 7) Block Extension
| **Actor** | System |
| :--- | :--- |
| **Description** | 승인된 예약자가 존재할 경우 기존 대여자의 연장 신청 기능을 자동으로 차단한다. |

### 8) Search & Filter
| **Actor** | Buyer/Borrower |
| :--- | :--- |
| **Description** | 물품 카테고리, 거래 방식(매매/대여), 예약 가능 여부 등 필터를 적용하여 검색한다. |

### 9) Request Transaction
| **Actor** | Buyer/Borrower |
| :--- | :--- |
| **Description** | 특정 물품에 대해 구매 요청 또는 대여/예약 요청을 공급자에게 전송한다. |

### 10) Manage Requests Std
| **Actor** | Seller/Lender |
| :--- | :--- |
| **Description** | 본인의 물품에 들어온 거래 및 연장/예약 요청을 대시보드에서 통합 관리한다. |

### 11) Confirm Pickup/Return
| **Actor** | Seller/Lender, Buyer/Borrower |
| :--- | :--- |
| **Description** | 대면 거래 후 물품 수령 및 반납 완료를 상호 확인하여 시스템 상태를 업데이트한다. |

### 12) Transaction Review
| **Actor** | Seller/Lender, Buyer/Borrower |
| :--- | :--- |
| **Description** | 거래 종료 후 상대방의 매너 및 물품 보존 상태에 대한 별점과 후기를 기록한다. |

### 13) System Monitoring
| **Actor** | Admin |
| :--- | :--- |
| **Description** | 전체 거래 데이터를 감시하여 부정 거래나 부적절한 게시물을 관리한다. |
