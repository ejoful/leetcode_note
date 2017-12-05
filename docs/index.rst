.. leetcode note documentation master file, created by
   sphinx-quickstart on Mon Dec  4 13:39:02 2017.
   You can adapt this file completely to your liking, but it should at least
   contain the root `toctree` directive.

=====================================
Leetcode note |version| documentation
=====================================


**版权声明**

本笔记提供的内容用于个人学习、研究或欣赏，以及其他非商业性或非盈利性用途，但同时应遵守著作权法及其他相关法律的规定，不得侵犯作者的合法权利。除此以外，将本笔记任何内容或服务用于其他用途时，须征得作者本人的书面许可，并支付报酬。

**内容简介**

本笔记既适用于准备去国外找工作的码农，也适用于在国内找工作的码农，或者想参加ACM算法竞赛的新手。

本笔记包含了 `LeetCode`_ 算法分类下共计741多道题目，使用C++ 11编写，所有代码都在LeetCode上测试通过，精心编写，并给出了详细的分析过程，解题思路，考点。编码规范使用 
`Google C++ Style Guide`_，适合读者反复揣摩，模仿，甚至在纸上默写。

本笔记假定读者已经学过 `\《C++ Primer(中文版)(第5版)\》`_ [#]_, `\《数据结构与算法\》`_ [#]_,这两本书，熟练掌握C++。

.. _LeetCode: https://leetcode.com/problemset/algorithms/
.. _Google C++ Style Guide: https://google.github.io/styleguide/cppguide.html
.. _《数据结构与算法》: https://amazon.cn/gp/product/B004VK8XL8/ref=as_li_tl?ie=UTF8&camp=536&creative=3200&creativeASIN=B004VK8XL8&linkCode=as2&tag=qinlinghk-23&linkId=15885f79c196609fc991774d2b035041
.. _《C++ Primer(中文版)(第5版)》: https://amazon.cn/gp/product/B00ESUIL0O/ref=as_li_tl?ie=UTF8&camp=536&creative=3200&creativeASIN=B00ESUIL0O&linkCode=as2&tag=qinlinghk-23&linkId=af2fdc902850a4cb8493ea1fcbd1e614

.. rubric:: Footnotes
.. [#] 《C++ Primer(中文版)(第5版)\》, 斯坦利·李普曼 (Stanley B. Lippman) (作者),‎ 约瑟·拉乔伊 (Josee Lajoie) (作者),‎ 芭芭拉·默 (Barbara E. Moo) (作者),‎ 王刚 (译者),‎ 杨巨峰 (译者), 电子工业出版社
.. [#] 《数据结构与算法》, 张铭，王腾蛟，赵海燕，高等教育出版社，2008年6月。普通高等教育“十一五”国家级规划教材。

*text*
**text**
sample::

	class Solution {
	public:
	    vector<int> singleNumber(vector<int>& nums) {
		int length = nums.size();
		
		// get the xor result of the array, b ^ c
		int xor_result = 0;
		for(int i =0; i< length; i++) {
		    xor_result ^= nums[i];
		}
		
		// get the K of first bit, which equals 1
		int first_one_index = 0;
		for(first_one_index =0; first_one_index< 32; first_one_index++) {
		    if((xor_result>>first_one_index) & 1 == 1) {
		        break;
		    }
		}
		
		// use k to split the array into two part
		// xor the sub array, if the element's Kth bit also equals 1, b
		int xor_twice = 0;
		for(int i =0; i< length; i++) {
		    if((nums[i]>>first_one_index) & 1 == 1) {
		        xor_twice ^= nums[i];
		    }
		}
		
		// with b, easy to get c by math
		vector<int> result = {xor_twice, xor_result ^ xor_twice };        
		return result;
	    }
	};


.. toctree::
   :maxdepth: 2



Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

