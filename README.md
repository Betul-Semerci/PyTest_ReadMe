# PyTest

PyTest bir Python test çerçevesidir ve test fonksiyonlarını ve modüllerini yönetmek için bir dizi özellik ve decorator sağlar. <br/>
İşte pytest kullanırken sıkça kullanılan bazı decorator'ler:

**@pytest.mark.parametrize**

Parametreli testler, geliştiricinin aynı testi farklı değerler üzerinde tekrar tekrar çalıştırmasına olanak tanır. <br/>
Parametreli test, veriye dayalı test yapmak istediğimiz zamandır.  <br/>

Örneğin, giriş sayfasını veya işlemini, örneğin 1000 farklı kullanıcı adı ve şifre koşulu gibi birden fazla giriş değeriyle test etmek istiyoruz. <br/>

Bu, daha fazla test kodu eklemenize gerek kalmadan kapsamı artırmanıza olanak tanır.  

import pytest

@pytest.mark.parametrize("input, expected", [(1, 2), (2, 3), (3, 4)])  <br/>
def test_increment(input, expected):
    result = input + 1
    assert result == expected

**@pytest.mark.skip ve @pytest.mark.skipif**

Bu decorator'ler, belirli testleri atlamak veya koşullu olarak atlamak için kullanılır.

import pytest

@pytest.mark.skip(reason="Test skipped temporarily") <br/>
def test_skip_example(): <br/>
    pass

@pytest.mark.skipif(sys.version_info < (3, 6), reason="Does not run on Python versions before 3.6") <br/>
def test_skipif_example(): <br/>
    pass

**@pytest.fixture**

Bu decorator, bir test fonksiyonuna veya bir başka fixture'a bağımlılık oluşturan bir işlevi belirtmek için kullanılır. <br/>
Fixtures, testler arasında paylaşılan durumu yönetmek için kullanılır.

import pytest

@pytest.fixture <br/>
def setup(): <br/>
    # Fixture setup code <br/>
    yield <br/>
    # Fixture teardown code <br/>

def test_example(setup): <br/>
    # Test code using the 'setup' fixture

**@pytest.mark.xfail**

import pytest

@pytest.mark.xfail <br/>
def test_expected_failure(): <br/>
    assert 1 == 2


Bu decorator, bir testin başarısız olmasını bekleyen bir işaret koymak için kullanılır. <br/>
Yani, test başarısız olacak, ancak bu bir hata olarak kabul edilmeyecek ve test sonucu başarılı olarak işaretlenecek.

• Bu decorator'ler, pytest ile test yazarken sıkça kullanılan ve test süitlerini düzenlemenizi sağlayan bazı temel araçlardır.

