# myvimrc

### 1.yaml and python 들여쓰기와 colorcolumn 설정 (vimrc)
- yaml 들여쓰기 규칙
- python 들여쓰기 규칙
- colorcorsor 활성화
- 실시간 search highlight 활성화와
> ~/.vimrc
```
syntax on
autocmd FileType yaml setlocal ts=2 sts=2 sw=2 et ai
autocmd FileType python setlocal ts=4 sts=4 sw=4 expandtab autoindent
autocmd CursorMoved,CursorMovedI * execute 'set colorcolumn=' . virtcol('.')
set hlsearch
set incsearch
```

### 2.bash history 용량 및 최적화 설정 (bashrc)
- 히스토리 크기 늘리기
- 중복된 명령어 저장 방지
- 특정 명령어 저장하지 않기 (ls, cd, pwd 등)
- 실시간으로 히스토리 저장 (즉각 반영)
- 히스토리 파일 동기화 (여러 터미널 간 공유)
- 검색 앞뒤로 하기
> ~/.bashrc
```
export HISTSIZE=100000       # 현재 세션에서 저장할 명령어 개수 (기본값 500~1000)
export HISTFILESIZE=200000   # ~/.bash_history 파일에 저장할 명령어 개수

export HISTCONTROL=ignoredups:erasedups  # 중복된 명령어 제거 (최근 것만 유지)

export HISTIGNORE="ls:cd:cd -:pwd:exit:clear"

export PROMPT_COMMAND="history -a; history -c; history -r; $PROMPT_COMMAND"

shopt -s histappend

stty -ixon
```
