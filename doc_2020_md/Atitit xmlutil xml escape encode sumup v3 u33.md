Atitit xmlutil xml escape encode sumup v3 u33



   //   org.testng.xml.XmlUtils
   // 	ch.qos.logback.core.joran.spi.XMLUtil	XMLUtil.
   // 	import com.aliyuncs.utils.XmlUtils;	XmlUtils.
    //	import org.testng.xml.XmlUtils;  XmlUtils.    //	
    //	 com.sun.org.apache.xml.internal.security.utils.XMLUtils 
    //	com.sun.xml.internal.ws.util.xml.XmlUtil.
    	//only blow can ok has escape method
     //org.testng.reporters.XMLUtils.escape(input)
System.out.println(cn.hutool.core.util.XmlUtil.escape("aaa=1&bbb=2"));	;



 /**
     * Escape the following characters {@code " ' & < >} with their XML entities, e.g.
     * {@code "bread" & "butter"} becomes {@code &quot;bread&quot; &amp; &quot;butter&quot}.
     * Notes:<ul>
     * <li>Supports only the five basic XML entities (gt, lt, quot, amp, apos)</li>
     * <li>Does not escape control characters</li>
     * <li>Does not support DTDs or external entities</li>
     * <li>Does not treat surrogate pairs specially</li>
     * <li>Does not perform Unicode validation on its input</li>
     * </ul>
     *
     * @param orig the original String
     * @return A new string in which all characters that require escaping
     *         have been replaced with the corresponding XML entities.
     * @see #escapeControlCharacters(String)
     */
//    public static String escapeXml(String orig) {
//        return collectReplacements(orig, new Closure<String>(null) {
//            public String doCall(Character arg) {
//                switch (arg) {
//                    case '&':
//                        return "&amp;";
//                    case '<':
//                        return "&lt;";
//                    case '>':
//                        return "&gt;";
//                    case '"':
//                        return "&quot;";
//                    case '\'':
//                        return "&apos;";
//                }
//                return null;
//            }
//        });
//    }
