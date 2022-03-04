---
layout: single
title: "React Fragment Map Key"
excerpt: "Fragments에도 key를 줄 수 있다."

categories:
  - React
tags:
  - [React, Fragment, ReactMap]

toc: true
toc_sticky: true
 
date: 2022-03-05
last_modified_at: 2022-03-05
---

# React Fragment

 - Fragments는 DOM에 별도의 노드를 추가하지 않고 여러 자식을 그룹화 가능
 - Fragments에도 key를 줄 수 있다.

1. 문제 코드  
 \- 해당 코드는 Fragments를 그룹화하는 문법이라 생각 내부 컴포넌트에 key 작성  
\>\> key가 없다는 오류 발생
```React
function SideMenuLayout({ menus }) {
    return (
            <AsideWrap>
                {menus.map((menu, i) => {
                    <>
                        <SideTitle key={menu.title}>
                            {menu.icon} {menu.title}
                        </SideTitle>
                        <hr />
                    </>
                })}
            </AsideWrap>
    );
}
```
2. 해결 코드  
    \- Fragment에 Key 전달  
```React
function SideMenuLayout({ menus }) {
    return (
            <AsideWrap>
                {menus.map((menu, i) => {
                    <Fragment key={menu.title}>
                        <SideTitle>
                            {menu.icon} {menu.title}
                        </SideTitle>
                        <hr />
                    </Fragment>
                })}
            </AsideWrap>
    );
}
```
