####Javascript进阶
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