# 220630

* Transferring Ownership
<!--more-->
# Udacity
## Transferring Ownership
* R.30: Take smart pointers as parameters only to explicitly express lifetime semantic
* R.32: Take a unique_ptr parameter to express that a function assumes ownership of a widget
	* 기본 아이디어 -> 그것의 유일한 인스턴스만 존재하도록 하기 위함
	* 이것이 복사 할 수 없는 이유이고, 오로지 `std::move`함수를 통해 이동시켜야 함
* R.34: Take a shared_ptr parameter to express that a fnction is part owner
* R.33: Take a unique_ptr& parameter to express that a function reseats the widget
* R.35: Take a shared_ptr& parameter to express that a function might reseat the shared pointer
* Returning smart pointers from functions

