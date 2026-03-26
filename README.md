# 1. Conceptualization: Major Share (전공 자산 선순환 네트워크)

**학번:** 202XXXXX  
**이름:** 배진우  
**이메일:** [진우님의 이메일 주소]

## [ Revision history ]
| Revision date | Version # | Description | Author |
| :--- | :--- | :--- | :--- |
| 2026/03/22 | 1.00 | 최초 초안 작성 및 대여/예약 로직 상세화 Std No_Name.hwp] | 배진우 |
| 2026/03/26 | 1.10 | 용어 일관성 수정 및 Mermaid 다이어그램 코드 삽입 | 배진우 |

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
- **Project background & Motivation:** 대학 전공 서적 및 실험 기자재는 단가가 높음에도 특정 학기에만 사용되는 '고비용 저효율' 특성을 가집니다 Std No_Name.hwp]. 현재의 중고 거래는 일회성 매매에 치중되어 단기 사용이 필요한 학생들에게 경제적 부담을 주며, 개인 간 대여는 반납 관리와 예약자 간 분쟁으로 활성화되지 못하고 있습니다 Example 4.pdf].
- **Goal:** 'Major Share'는 전공 자산의 **매매(Sale)**와 **대여(Rental)**를 통합 관리하는 플랫폼입니다. 특히 실시간 예약 및 자동 연장 제어 시스템을 통해 자원 독점을 방지하고 활용도를 극대화하여 공정한 선순환 경제를 형성하는 것이 목표입니다 Project plan.pdf].
- **Target market:** 영남대학교 컴퓨터공학부 재학생 및 전공 기자재 공유가 필요한 공과대학 구성원.

## 2. System context diagram

<img width="818" height="618" alt="system_context_diagram" src="https://github.com/user-attachments/assets/53367d8c-9092-499e-a87a-466789316d78" />


## 3. Use case list

### 1) Register Item Std No_Name.hwp]
| **Actor** | Seller/Lender |
| :--- | :--- |
| **Description** | 판매 또는 대여하고자 하는 전공 자산의 상세 정보(상태, 가격, 대여 기간 등)를 시스템에 등록한다. |

### 2) Request Extension
| **Actor** | Buyer/Borrower |
| :--- | :--- |
| **Description** | 대여 중인 물품의 기간 연장을 신청한다. 단, 예약 대기자가 없을 때만 시스템에 의해 활성화된다. |

### 3) Reserve Item
| **Actor** | Buyer/Borrower |
| :--- | :--- |
| **Description** | 현재 타 사용자가 이용 중인 물품에 대해 차기 대여 예약을 신청한다. |

### 4) Accept Reservation
| **Actor** | Seller/Lender |
| :--- | :--- |
| **Description** | 들어온 예약 신청 목록을 확인하고 특정 사용자의 예약 요청을 승인하여 우선권을 부여한다. |

### 5) Auto-Succession Project plan.pdf]
| **Actor** | System |
| :--- | :--- |
| **Description** | 기존 대여자의 반납이 완료되면 승인된 차기 예약자에게 자동으로 대여 권한 및 알림을 승계한다. |

### 6) Block Extension
| **Actor** | System |
| :--- | :--- |
| **Description** | 승인된 예약자가 존재할 경우 기존 대여자의 연장 신청 기능을 자동으로 차단한다. |

### 7) Search & Filter Example 2.pdf]
| **Actor** | Buyer/Borrower |
| :--- | :--- |
| **Description** | 물품 카테고리, 거래 방식(매매/대여), 예약 가능 여부 등 필터를 적용하여 검색한다. |

### 8) Request Transaction
| **Actor** | Buyer/Borrower |
| :--- | :--- |
| **Description** | 특정 물품에 대해 구매 요청 또는 대여/예약 요청을 공급자에게 전송한다. |

### 9) Manage Requests Std No_Name.hwp]
| **Actor** | Seller/Lender |
| :--- | :--- |
| **Description** | 본인의 물품에 들어온 거래 및 연장/예약 요청을 대시보드에서 통합 관리한다. |

### 10) Confirm Pickup/Return
| **Actor** | Seller/Lender, Buyer/Borrower |
| :--- | :--- |
| **Description** | 대면 거래 후 물품 수령 및 반납 완료를 상호 확인하여 시스템 상태를 업데이트한다. |

### 11) Transaction Review Example 3.pdf]
| **Actor** | Seller/Lender, Buyer/Borrower |
| :--- | :--- |
| **Description** | 거래 종료 후 상대방의 매너 및 물품 보존 상태에 대한 별점과 후기를 기록한다. |

### 12) System Monitoring
| **Actor** | Admin |
| :--- | :--- |
| **Description** | 전체 거래 데이터를 감시하여 부정 거래나 부적절한 게시물을 관리한다. |
