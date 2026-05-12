---
tags: [집합론, Peano, 자연수]
분야: 집합론 기초
---

# 02 — Peano 공리

← [[01 - 수리논리학의 기초]] | 다음 → [[03 - 집합의 개념]]

---

## Peano 공리

> [!axiom] Peano 공리 (PA)
> 다음 다섯 가지 공리를 만족하는 집합이 존재하고, 그 집합을 $\mathbb{N}$으로 나타낸다.
> $\mathbb{N}$의 원소를 **자연수(natural)**라 부른다.
>
> - **PA1.** $1$이라는 원소가 $\mathbb{N}$에 존재한다.
> - **PA2.** 임의의 $n \in \mathbb{N}$에 대하여, $n$과 다른 후임자(successor) $n^{+}$가 $\mathbb{N}$에 유일하게 존재한다.
> - **PA3.** 임의의 $n \in \mathbb{N}$에 대하여, $n^{+} \neq 1$이다.
> - **PA4.** 임의의 $n, m \in \mathbb{N}$에 대하여, $n^{+} = m^{+} \Rightarrow n = m$이다.
> - **PA5.** $P$가 다음 두 조건을 만족하는 $\mathbb{N}$의 부분집합일 때, $P = \mathbb{N}$이다.
>   - (i) $1 \in P$
>   - (ii) $n \in P \Rightarrow n^{+} \in P$

> [!theorem] Peano 구조의 유일성
> 두 구조 $(\mathbb{N}, 1, S)$과 $(\mathbb{N}', 1', S')$가 둘 다 Peano 공리를 만족하면,
> $f : \mathbb{N} \to \mathbb{N}'$ 중 오직 하나의 전단사 함수가 존재하여
> $$f(1) = 1', \qquad f(S(n)) = S'(f(n)) \quad (\forall n \in \mathbb{N})$$
> 따라서 두 구조는 동형이다.

> [!proof]- 증명
> **(1) $f$의 재귀적 정의 및 존재**
>
> $f(1) = 1'$, 그리고 $f(S(n)) := S'(f(n))$으로 정의한다.
> 집합 $A = \{n \in \mathbb{N} \mid f(n)\text{이 정의됨}\}$을 잡으면 $1 \in A$이고 $n \in A \Rightarrow S(n) \in A$이므로 PA5에 의해 $A = \mathbb{N}$.
>
> **(2) 역함수 $g$의 정의**
>
> 같은 방식으로 $g : \mathbb{N}' \to \mathbb{N}$을 $g(1') = 1$, $g(S'(x')) := S(g(x'))$으로 재귀 정의한다.
>
> **(3) $g \circ f = \mathrm{id}_{\mathbb{N}}$ 및 $f \circ g = \mathrm{id}_{\mathbb{N}'}$**
>
> 기저: $g(f(1)) = g(1') = 1$.
> 귀납단계: $g(f(S(n))) = g(S'(f(n))) = S(g(f(n))) = S(n)$ (귀납 가정 사용).
> 따라서 $g \circ f = \mathrm{id}_{\mathbb{N}}$. 동일 절차로 $f \circ g = \mathrm{id}_{\mathbb{N}'}$.
>
> **(4) 유일성**
>
> $h : \mathbb{N} \to \mathbb{N}'$이 같은 조건을 만족하면 귀납법으로 모든 $n$에 대해 $h(n) = f(n)$. $\square$

---

## 수학적귀납법

Peano 공리 PA5는 수학적 귀납법의 공리적 근거이다.

"$0$에서 성립하고, 어떤 칸에서 성립하면 다음 칸에서도 성립한다"고 확인하면, PA5가 그 성질을 모든 자연수에 전파한다는 것을 보장한다.

> [!definition] 수학적귀납법
> **Peano 공리(요약)**: $0$의 존재, 각 수의 후계자 존재, $0$은 어떤 수의 후계자가 아니다, 서로 다른 수는 서로 다른 후계자, 그리고 귀납 공리.
>
> **수학적 귀납법**: $P(0)$을 보이고, $\forall k\,(P(k) \Rightarrow P(k+1))$을 보이면 $\forall n\, P(n)$이 성립한다.

**왜 수학적 귀납법이 증명이 되는가?**

성질 $P(n)$이 성립하는 수들의 집합 $X = \{n \in \mathbb{N} : P(n)\}$을 생각하자.
$P(0)$과 귀납단계를 보였다면 $0 \in X$이고 $n \in X \Rightarrow n+1 \in X$이므로,
PA5(귀납 공리)에 의해 $X = \mathbb{N}$. 따라서 모든 자연수에 대해 $P(n)$이 성립한다.

---

## 자연수의 덧셈

> [!definition] 자연수의 덧셈
> 임의의 $x, y \in \mathbb{N}$에 대하여, 덧셈을 귀납적으로 정의한다:
> $$1 + x := x^{+}, \quad x + 1 := x^{+}, \quad x^{+} + y := (x + y)^{+}$$

> [!theorem] 덧셈의 기본 법칙
> 임의의 $x, y, z \in \mathbb{N}$에 대하여:
>
> **(1)** $x + (y + z) = (x + y) + z$ — 결합법칙
>
> **(2)** $x + y = y + x$ — 교환법칙
>
> **(3)** $x + z = y + z \Rightarrow x = y$ — 소거법칙

> [!definition] 자연수의 대소 관계
> 임의의 $x, y \in \mathbb{N}$에 대하여, $x = y + z$를 만족하는 $z \in \mathbb{N}$이 존재할 때 $x > y$라 한다.

> [!theorem] 전순서 및 삼일률
> **(1)** $x > y$이고 $y > z$이면 $x > z$ — 추이율
>
> **(2)** 임의의 $x, y \in \mathbb{N}$에 대해 다음 중 단 한 가지만 성립한다 — 삼일률
> $$x > y, \quad x = y, \quad x < y$$

> [!lemma] 최소원소의 존재
> 공집합이 아닌 $\mathbb{N}$의 부분집합 $A$는 최소원소를 가진다.

> [!definition] 위로 유계
> 공집합이 아닌 $\mathbb{N}$의 부분집합 $A$에 대하여, 모든 $m \in A$에 대해 $m < k_0$를 만족하는 $k_0 \in \mathbb{N}$가 존재하면 $A$가 **위로 유계**라고 한다.

---

## 자연수의 곱셈

> [!definition] 자연수의 곱셈
> 임의의 $x, y \in \mathbb{N}$에 대하여, 곱셈을 귀납적으로 정의한다:
> $$1 \cdot x := x, \quad x \cdot 1 := x, \quad x^{+} \cdot y := x \cdot y + y$$

> [!theorem] 곱셈의 기본 법칙
> 임의의 $x, y, z \in \mathbb{N}$에 대하여:
>
> **(1)** $x(yz) = (xy)z$ — 결합법칙
>
> **(2)** $xy = yx$ — 교환법칙
>
> **(3)** $xz = yz \Rightarrow x = y$ — 소거법칙
>
> **(4)** $x(y+z) = xy + xz$ — 분배법칙

> [!theorem] 나눗셈 알고리즘
> 임의의 $m, l \in \mathbb{N}$에 대하여 $1 \leq m \leq l$일 때,
> $$l = mn \quad \text{또는} \quad l = mn + r, \quad 1 \leq r < m$$
> 을 만족하는 $n, r \in \mathbb{N}$이 **유일하게** 존재한다.

> [!proof]- 증명 (나눗셈 알고리즘)
> **존재성**: $A = \{k \in \mathbb{N} \mid mk \leq l\}$로 정의하면 $1 \in A$이므로 공집합이 아니다.
> $A$의 최대원소 $n$이 존재하고, $mn \leq l < mn^{+} = mn + m$.
> $l \neq mn$이면 $l = mn + r,\; 1 \leq r < m$인 $r$이 존재한다.
>
> **유일성**: $n \neq n'$이라 가정하면 $n < n'$ 또는 $n' < n$인데,
> 어느 경우든 $mn^{+} \leq mn' \leq l = mn + r < mn + m = mn^{+}$가 되어 모순. $\square$
