Atitit java code parse  graph meth by pmd
	public static String getValWarpFmt(String cType, Object object) {
		if (cType.equals("BIGINT")) {
			return object.toString();
		}

		if (cType.equals("TINYINT") || cType.equals("INT"))
			return object.toString();
		if (cType.equals("VARCHAR"))
			return "'" + object.toString() + "'";
		if (cType.equals("DATETIME")) {
			if (object instanceof Map)
				return ((Map) object).get("exp").toString();
			else
				return "'" + object.toString() + "'";

		}





Ast tool   xpath designer

