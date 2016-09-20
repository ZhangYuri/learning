##Javascript进阶
###函数
####1.arguments



	function add() {
	    var sum = 0;
	    for (var i = 0, j = arguments.length; i < j; i++) {
	        sum += arguments[i];
	    }
	    return sum;
	}
	
	add(2, 3, 4, 5); // 14
####2.apply()
	function avg() {
	    var sum = 0;
	    for (var i = 0, j = arguments.length; i < j; i++) {
	        sum += arguments[i];
	    }
	    return sum / arguments.length;
	}
	avg(2, 3, 4, 5); // 3.5
	avg.apply(null, [2, 3, 4, 5]); // 3.5

####3.递归调用
	
	function countChars(elm) {
	    if (elm.nodeType == 3) { // 文本节点
	        return elm.nodeValue.length;
	    }
	    var count = 0;
	    for (var i = 0, child; child = elm.childNodes[i]; i++) {
	        count += countChars(child);
	    }
	    return count;
	}