if (boardResponseVo.getRequestPage() > 1) {
            if (boardResponseVo.isSearchResult()) {
                out.println("<span><a href=\"search?id=" + id + "&page=1&keyword=" + keyword + "&what=" + what + "\">처음</a></span>");
            } else {
                out.println("<span><a href=\"board?id=" + id + "&page=1\">처음</a></span>");
            }
        }
        for (int i = boardResponseVo.getStartPage(); i <= boardResponseVo.getEndPage(); i++) {
            if (i == boardResponseVo.getRequestPage()) {
                out.println("<span><strong>" + i + "</strong></span>");
            } else {
                if (boardResponseVo.isSearchResult()) {
                    out.println("<span><a href=\"search?id=" + id + "&page=" + i + "&keyword=" + keyword + "&what=" + what + "\">" + i + "</a></span>");
                } else {
                    out.println("<span><a href=\"board?id=" + id + "&page=" + i + "\">" + i + "</a></span>");
                    // <span><a href="board?id=fre&page=1">1</a></span>
                    // <span><a href="board?id=fre&page=2">2</a></span>
                    // <span><a href="board?id=fre&page=3">3</a></span>
                    // <span><a href="board?id=fre&page=4">4</a></span>
                    // <span><a href="board?id=fre&page=5">5</a></span>
                }
                //out.println(String.format("<span><a href=\"board?id=%s&page=%d\">%d</a></span>", id, i, i));
            }
        }
        if (boardResponseVo.getMaxPage() > boardResponseVo.getRequestPage()) {
            if (boardResponseVo.isSearchResult()) {
                out.println("<span><a href=\"search?id=" + id + "&page=" + boardResponseVo.getMaxPage() + "&keyword=" + keyword + "&what=" + what + "\">끝</a></span>");
            } else {
                out.println("<span><a href=\"board?id=" + id + "&page=" + boardResponseVo.getMaxPage() + "\">끝</a></span>");
            }
        }
        out.println("</div>");
        if (boardResponseVo.isSearchResult()) {
            out.println("<a href=\"board?id=" + request.getParameter("id") + "\">검색 초기화</a>");
        }
    }
