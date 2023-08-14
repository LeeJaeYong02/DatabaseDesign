# DatabaseDesign Term Project

데이터베이스 설계 순서

[1. 요구 조건 분석](#요구-조건-분석)
<br/>
[2. 개념적 설계](#개념적-설계)
<br/>
[3. 논리적 설계](#논리적-설계)
<br/>
[4. 물리적 설계](#물리적-설계)
<br/>
[5. 구현](#구현)

---

## 요구 조건 분석

- 사용자의 요구 사항을 분석
- 요구 조건 명세서 작성

어떤 시스템을 구축할 것인지, 어떠한 데이터와 기능이 필요한지를 조사하고 분석하여 요구 조건 명세서를 작성한다. <br/>
아래는 가상으로 만든 요구 조건 명세서다.

[1_요구사항명세서.zip](https://github.com/LeeJaeYong02/DatabaseDesign/files/12335037/1_.zip)
<details>
<summary>쇼핑몰 사이트 데이터베이스 요구 사항 명세서 (접기/펼치기)</summary>

목적

이 명세서는 쇼핑몰 사이트의 데이터베이스를 설계하고 구축하기 위한 요구 사항을 정의합니다. 데이터베이스는 제품, 주문, 고객 정보 등을 효율적으로 관리하고 웹 애플리케이션과 연동하여 원활한 쇼핑 경험을 제공해야 합니다.

기능적 요구 사항

1.  제품 관리
1.1. 제품 정보(제품명, 설명, 가격, 재고량 등)를 저장할 수 있어야 합니다.
1.2. 카테고리 및 서브카테고리를 정의하고 제품을 분류할 수 있어야 합니다.
1.3. 제품의 이미지 및 추가 정보를 첨부할 수 있어야 합니다.

2. 고객 관리
2.1. 고객 정보(이름, 이메일, 주소, 연락처 등)를 저장할 수 있어야 합니다.
2.2. 고객은 회원 가입을 통해 계정을 생성하고 로그인할 수 있어야 합니다.
2.3. 로그인한 고객은 주문 내역을 조회하고 프로필을 관리할 수 있어야 합니다.

3. 주문 처리
3.1. 고객은 제품을 선택하여 주문할 수 있어야 합니다.
3.2. 주문 내역(주문 번호, 주문 일자, 결제 상태 등)을 저장하고 조회할 수 있어야 합니다.
3.3. 주문한 제품의 재고량이 자동으로 감소되어야 합니다.
3.4. 주문 상태를 변경하여 주문 처리 과정을 추적할 수 있어야 합니다.

4. 장바구니
4.1. 로그인한 고객은 제품을 장바구니에 추가하고 관리할 수 있어야 합니다.
4.2. 장바구니에서 제품을 주문으로 이동하거나 삭제할 수 있어야 합니다.

5. 리뷰 및 평점
5.1. 고객은 제품에 대한 리뷰를 작성하고 평점을 부여할 수 있어야 합니다.
5.2. 리뷰와 평점은 해당 제품 페이지에 표시되어야 합니다.

비기능적 요구 사항

6. 보안
6.1. 고객의 개인정보와 결제 정보는 암호화되어 저장되어야 합니다.
6.2. 관리자와 고객 간에 적절한 접근 권한을 설정하여 데이터 보안을 유지해야 합니다.
7. 성능
7.1. 데이터베이스 쿼리는 효율적으로 처리되어야 하며, 제품 검색 및 주문 처리가 빠르게 이루어져야 합니다.
7.2. 서버의 부하를 최소화하기 위해 캐싱 메커니즘을 고려할 수 있습니다.

8. 확장성
8.1. 시스템은 향후 증가하는 데이터 양과 트래픽을 처리할 수 있도록 설계되어야 합니다.
8.2. 수평 확장을 위한 방법을 고려하여 데이터베이스 구조를 설계해야 합니다.

9. 가용성
9.1. 데이터베이스 서버의 가용성을 보장하기 위해 복구 메커니즘과 백업 전략을 마련해야 합니다.
</details>

---

## 개념적 설계

- DBMS에 독립적인 개념 스키마 설계(E-R 모델)
- 트랜잭션 모델링

---

## 논리적 설계

- DBMS에 맞는 스키마 설계
- 트랜잭션 인터페이스 설계

[2,3_ERD.zip](https://github.com/LeeJaeYong02/DatabaseDesign/files/12335108/2.3_ERD.zip)

![image](https://github.com/LeeJaeYong02/DatabaseDesign/assets/66985977/dc50e421-1a75-4c79-a1f5-9ecd7137871f)

### 관계선 의미
![image](https://github.com/LeeJaeYong02/DatabaseDesign/assets/66985977/d7ae73d9-a941-4a41-ac76-55aa2d403041)

---

## 물리적 설계

- DBMS에 맞는 물리적 구조 설계
- 트랜잭션 세부 설계

---

## 구현

- 특정 DBMS의 DDL로 데이터베이스 생성
- 트랜잭션 작성

[5_구현.txt](https://github.com/LeeJaeYong02/DatabaseDesign/files/12335066/4_.txt)
<details>
<summary>스크립트 (접기/펼치기)</summary>

-- 고객
CREATE TABLE "TB_CUSTOMER" (
	"CUSTOMER_ID"       VARCHAR(20)  NOT NULL, -- 고객ID
	"CUSTOMER_NAME"     VARCHAR(50)  NULL,     -- 이름
	"CUSTOMER_EMAIL"    VARCHAR(40)  NULL,     -- 이메일
	"CUSTOMER_ADDRESS"  VARCHAR(255) NULL,     -- 주소
	"CUSTOMER_CNTCT"    VARCHAR(13)  NULL,     -- 연락처
	"CUSTOMER_PASSWORD" VARCHAR(20)  NULL,     -- 비밀번호
	"CUSTOMER_JOINED"   DATE         NULL      -- 가입일
);

-- 고객
ALTER TABLE "TB_CUSTOMER"
	ADD
		CONSTRAINT "PK_TB_CUSTOMER" -- 고객 기본키
		PRIMARY KEY (
			"CUSTOMER_ID" -- 고객ID
		);

-- 제품
CREATE TABLE "TB_PRODUCT" (
	"PRODUCT_ID"          NUMERIC(37)   NOT NULL, -- 제품ID
	"PRODUCT_NAME"        VARCHAR(200)  NULL,     -- 제품명
	"PRODUCT_EXPLANATION" CLOB          NULL,     -- 설명
	"PRODUCT_PRICE"       NUMERIC(10)   NULL,     -- 가격
	"PRODUCT_INVNT"       NUMERIC(10)   NULL,     -- 재고량
	"PRODUCT_IMAGE_URL"   VARCHAR(1000) NULL,     -- 이미지 URL
	"CATEGORY_ID"         NUMERIC(37)   NULL      -- 카테고리ID
);

-- 제품
ALTER TABLE "TB_PRODUCT"
	ADD
		CONSTRAINT "PK_TB_PRODUCT" -- 제품 기본키
		PRIMARY KEY (
			"PRODUCT_ID" -- 제품ID
		);

-- 카테고리
CREATE TABLE "TB_CATEGORY" (
	"CATEGORY_ID"   NUMERIC(37) NOT NULL, -- 카테고리ID
	"CATEGORY_NAME" VARCHAR(50) NULL      -- CATEGORY_NAME
);

-- 카테고리
ALTER TABLE "TB_CATEGORY"
	ADD
		CONSTRAINT "PK_TB_CATEGORY" -- 카테고리 기본키
		PRIMARY KEY (
			"CATEGORY_ID" -- 카테고리ID
		);

-- 서브카테고리
CREATE TABLE "TB_SUBCATEGORY" (
	"SUBCATEGORY_ID"   NUMERIC(37) NOT NULL, -- 서브카테고리ID
	"SUBCATEGORY_NAME" VARCHAR(50) NULL,     -- 서브카테고리명
	"CATEGORY_ID"      NUMERIC(37) NOT NULL  -- 카테고리ID
);

-- 서브카테고리
ALTER TABLE "TB_SUBCATEGORY"
	ADD
		CONSTRAINT "PK_TB_SUBCATEGORY" -- 서브카테고리 기본키
		PRIMARY KEY (
			"SUBCATEGORY_ID", -- 서브카테고리ID
			"CATEGORY_ID"     -- 카테고리ID
		);

-- 주문
CREATE TABLE "TB_ORDER" (
	"ORDER_ID"               NUMERIC(37)  NOT NULL, -- 주문ID
	"CUSTOMER_ID"            VARCHAR(20)  NULL,     -- 고객ID
	"ORDER_DATE"             DATE         NULL,     -- 주문일자
	"ORDER_PAYMENT_STATUS"   NUMERIC(1)   NULL,     -- 결제상태
	"ORDER_SHIPPING_ADDRESS" VARCHAR(255) NULL,     -- 배송주소
	"ORDER_TOTAL_AMUNT"      NUMERIC(10)  NULL      -- 총금액
);

-- 주문
ALTER TABLE "TB_ORDER"
	ADD
		CONSTRAINT "PK_TB_ORDER" -- 주문 기본키
		PRIMARY KEY (
			"ORDER_ID" -- 주문ID
		);

-- 주문상세
CREATE TABLE "TB_ORDER_DETAIL" (
	"ORDER_DETAIL_ID"     NUMERIC(37) NOT NULL, -- 주문상세ID
	"ORDER_ID"            NUMERIC(37) NOT NULL, -- 주문ID
	"PRODUCT_ID"          NUMERIC(37) NOT NULL, -- 제품ID
	"ORDER_DETAIL_QNTTY"  NUMERIC(10) NULL,     -- 주문 수량
	"ORDER_DETAIL_AMOUNT" NUMERIC(10) NULL      -- 주문 금액
);

-- 주문상세
ALTER TABLE "TB_ORDER_DETAIL"
	ADD
		CONSTRAINT "PK_TB_ORDER_DETAIL" -- 주문상세 기본키
		PRIMARY KEY (
			"ORDER_DETAIL_ID", -- 주문상세ID
			"ORDER_ID",        -- 주문ID
			"PRODUCT_ID"       -- 제품ID
		);

-- 장바구니
CREATE TABLE "TB_CART" (
	"CART_ID"     NUMERIC(37) NOT NULL, -- 카트ID
	"CUSTOMER_ID" VARCHAR(20) NULL      -- 고객ID
);

-- 장바구니
ALTER TABLE "TB_CART"
	ADD
		CONSTRAINT "PK_TB_CART" -- 장바구니 기본키
		PRIMARY KEY (
			"CART_ID" -- 카트ID
		);

-- 주문상세
CREATE TABLE "TB_CART_DETAIL" (
	"CART_DETAIL_ID"       NUMERIC(37) NOT NULL, -- 장바구니상세ID
	"PRODUCT_ID"           NUMERIC(37) NOT NULL, -- 제품ID
	"CART_ID"              NUMERIC(37) NULL,     -- 카트ID
	"CART_DETAIL_QUANTITY" NUMERIC(10) NULL      -- 수량
);

-- 주문상세
ALTER TABLE "TB_CART_DETAIL"
	ADD
		CONSTRAINT "PK_TB_CART_DETAIL" -- 주문상세 기본키2
		PRIMARY KEY (
			"CART_DETAIL_ID", -- 장바구니상세ID
			"PRODUCT_ID"      -- 제품ID
		);

-- 리뷰
CREATE TABLE "TB_REVIEW" (
	"REVIEW_ID"      NUMERIC(37)   NOT NULL, -- REVIEW_ID
	"CUSTOMER_ID"    VARCHAR(20)   NOT NULL, -- 고객ID
	"PRODUCT_ID"     NUMERIC(37)   NOT NULL, -- 제품ID
	"REVIEW_CONTENT" VARCHAR(1000) NULL,     -- REVIEW_CONTENT
	"REVIEW_RATING"  NUMERIC(1,1)  NULL,     -- REVIEW_RATING
	"REVIEW_DATE"    DATE          NULL      -- REVIEW_DATE
);

-- 리뷰
ALTER TABLE "TB_REVIEW"
	ADD
		CONSTRAINT "PK_TB_REVIEW" -- 리뷰 기본키
		PRIMARY KEY (
			"REVIEW_ID",   -- REVIEW_ID
			"CUSTOMER_ID", -- 고객ID
			"PRODUCT_ID"   -- 제품ID
		);

-- 제품
ALTER TABLE "TB_PRODUCT"
	ADD
		CONSTRAINT "FK_TB_CATEGORY_TO_TB_PRODUCT" -- 카테고리 -> 제품
		FOREIGN KEY (
			"CATEGORY_ID" -- 카테고리ID
		)
		REFERENCES "TB_CATEGORY" ( -- 카테고리
			"CATEGORY_ID" -- 카테고리ID
		);

-- 서브카테고리
ALTER TABLE "TB_SUBCATEGORY"
	ADD
		CONSTRAINT "FK_TB_CG_TO_TB_SUBCG" -- 카테고리 -> 서브카테고리
		FOREIGN KEY (
			"CATEGORY_ID" -- 카테고리ID
		)
		REFERENCES "TB_CATEGORY" ( -- 카테고리
			"CATEGORY_ID" -- 카테고리ID
		);

-- 주문
ALTER TABLE "TB_ORDER"
	ADD
		CONSTRAINT "FK_TB_CUSTOMER_TO_TB_ORDER" -- 고객 -> 주문
		FOREIGN KEY (
			"CUSTOMER_ID" -- 고객ID
		)
		REFERENCES "TB_CUSTOMER" ( -- 고객
			"CUSTOMER_ID" -- 고객ID
		);

-- 주문상세
ALTER TABLE "TB_ORDER_DETAIL"
	ADD
		CONSTRAINT "FK_TB_PD_TO_TB_ORDER_DETAIL" -- 제품 -> 주문상세
		FOREIGN KEY (
			"PRODUCT_ID" -- 제품ID
		)
		REFERENCES "TB_PRODUCT" ( -- 제품
			"PRODUCT_ID" -- 제품ID
		);

-- 주문상세
ALTER TABLE "TB_ORDER_DETAIL"
	ADD
		CONSTRAINT "FK_TB_ORDER_TO_TB_ORDER_DETAIL" -- 주문 -> 주문상세
		FOREIGN KEY (
			"ORDER_ID" -- 주문ID
		)
		REFERENCES "TB_ORDER" ( -- 주문
			"ORDER_ID" -- 주문ID
		);

-- 장바구니
ALTER TABLE "TB_CART"
	ADD
		CONSTRAINT "FK_TB_CUSTOMER_TO_TB_CART" -- 고객 -> 장바구니
		FOREIGN KEY (
			"CUSTOMER_ID" -- 고객ID
		)
		REFERENCES "TB_CUSTOMER" ( -- 고객
			"CUSTOMER_ID" -- 고객ID
		);

-- 주문상세
ALTER TABLE "TB_CART_DETAIL"
	ADD
		CONSTRAINT "FK_TB_PD_TO_TB_CART_DETAIL" -- 제품 -> 주문상세2
		FOREIGN KEY (
			"PRODUCT_ID" -- 제품ID
		)
		REFERENCES "TB_PRODUCT" ( -- 제품
			"PRODUCT_ID" -- 제품ID
		);

-- 주문상세
ALTER TABLE "TB_CART_DETAIL"
	ADD
		CONSTRAINT "FK_TB_CART_TO_TB_CART_DETAIL" -- 장바구니 -> 주문상세
		FOREIGN KEY (
			"CART_ID" -- 카트ID
		)
		REFERENCES "TB_CART" ( -- 장바구니
			"CART_ID" -- 카트ID
		);

-- 리뷰
ALTER TABLE "TB_REVIEW"
	ADD
		CONSTRAINT "FK_TB_PRODUCT_TO_TB_REVIEW" -- 제품 -> 리뷰
		FOREIGN KEY (
			"PRODUCT_ID" -- 제품ID
		)
		REFERENCES "TB_PRODUCT" ( -- 제품
			"PRODUCT_ID" -- 제품ID
		);

-- 리뷰
ALTER TABLE "TB_REVIEW"
	ADD
		CONSTRAINT "FK_TB_CUSTOMER_TO_TB_REVIEW" -- 고객 -> 리뷰
		FOREIGN KEY (
			"CUSTOMER_ID" -- 고객ID
		)
		REFERENCES "TB_CUSTOMER" ( -- 고객
			"CUSTOMER_ID" -- 고객ID
		);

-- Create Indexes
CREATE INDEX idx_Product_ProductName ON TB_PRODUCT(PRODUCT_NAME);
CREATE INDEX idx_Order_CustomerID ON TB_ORDER(CUSTOMER_ID);
CREATE INDEX idx_OrderDetail_OrderID ON TB_ORDER_DETAIL(ORDER_ID);
CREATE INDEX idx_OrderDetail_ProductID ON TB_ORDER_DETAIL(PRODUCT_ID);
CREATE INDEX idx_Cart_CustomerID ON TB_CART(CUSTOMER_ID);
CREATE INDEX idx_CartDetail_CartID ON TB_CART_DETAIL(CART_ID);
CREATE INDEX idx_CartDetail_ProductID ON TB_CART_DETAIL(PRODUCT_ID);
CREATE INDEX idx_Review_CustomerID ON TB_REVIEW(CUSTOMER_ID);
CREATE INDEX idx_Review_ProductID ON TB_REVIEW(PRODUCT_ID);
CREATE INDEX idx_Subcategory_CategoryID ON TB_SUBCATEGORY(CATEGORY_ID);
</details>

![5_데이터베이스 실제 테이블](https://github.com/LeeJaeYong02/DatabaseDesign/assets/66985977/1f36c9d4-a8da-4868-9eca-42449303c9ae)

---
